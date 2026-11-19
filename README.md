# 🔓 CyberDecoder

**Boîte à outils de décodage, de chiffrement et de hachage qui tourne dans le navigateur, inspirée de CyberChef.**

👉 **Démo en ligne : [vbenji23.github.io/CyberDecoder](https://vbenji23.github.io/CyberDecoder/)**

CyberDecoder permet d'enchaîner des opérations (une « recette ») et de voir le résultat changer en direct. Il sert à résoudre des défis CTF, à analyser des jetons ou à décoder des données suspectes rencontrées pendant un audit.

> Tout est calculé localement, en JavaScript. Aucune donnée n'est envoyée à un serveur.

---

## ✨ Fonctionnalités

- **Recette d'opérations en chaîne** : on ajoute des étapes, on les réordonne, on les met en pause ou on les supprime.
- **Résultat en direct** à chaque frappe, avec la taille en octets et le temps de calcul.
- **Détection automatique** : l'outil reconnaît la forme de la sortie (Base64, hex, JWT, binaire, Morse…) et propose l'étape suivante.
- **Détection de flag** : il signale quand la sortie contient un `FLAG{...}`.
- **Recettes prêtes** : défi CTF, analyse de JWT, XOR caché, empreintes de mot de passe.
- **Export et import** des recettes en JSON.
- **Sauvegarde locale** de la dernière recette et de l'entrée (localStorage).
- Interface responsive, avec un thème clair et un thème sombre.

## 🧰 Opérations disponibles

| Catégorie | Opérations |
|---|---|
| **Encodage** | Base64, Base32, Hexadécimal, Binaire, Décimal, Encodage URL, Entités HTML, Morse |
| **Chiffrement** | ROT13, César / ROT-N, force brute César, XOR (clé texte ou hex), force brute XOR sur 1 octet, Vigenère |
| **Hachage** | MD5 (implémenté à la main), SHA-1, SHA-256, SHA-512 (Web Crypto API) |
| **Analyse** | Décodeur JWT (détecte `alg: none` et l'expiration), JSON lisible, fréquence des caractères, extraction des chaînes lisibles |
| **Texte** | Inverser, majuscules, minuscules, retirer les espaces |

## 🚀 Exemple

Entrée :
```
U1lOVHtvdnJhaXJhaHJfcW5hZl9wbG9yZXFycGJxcmV9
```
Recette : `Depuis Base64` → `ROT13`

Sortie :
```
FLAG{bienvenue_dans_cyberdecoder}
```

## 🛠️ Technique

- **HTML, CSS et JavaScript natifs**, sans framework ni dépendance, dans un seul fichier.
- Toutes les opérations travaillent sur des **octets** (`Uint8Array`), si bien que les données binaires survivent à toute la chaîne (par exemple après un XOR).
- Les sorties non UTF-8 s'affichent automatiquement en hexadécimal.
- **MD5** est réimplémenté à partir de la RFC 1321 ; les **SHA** passent par `crypto.subtle`.
- Le traitement est asynchrone, et les calculs obsolètes sont ignorés quand on tape vite.

## 📦 Lancer en local

```bash
git clone https://github.com/vbenji23/CyberDecoder.git
cd CyberDecoder
# ouvrir index.html dans un navigateur
```

> Les fonctions SHA ont besoin d'un contexte sécurisé (HTTPS ou `localhost`). Si tu ouvres le fichier directement, MD5 et le reste fonctionnent quand même.

## 🎯 Ce que j'ai appris

- Le fonctionnement interne des encodages (Base64, Base32) au niveau du bit
- Le chiffrement XOR et ses faiblesses face à la force brute
- La structure d'un JWT et ses failles classiques (`alg: none`)
- L'algorithme MD5 et l'API Web Crypto
- La manipulation de données binaires en JavaScript

## 👤 Auteur

**Benjamin Vincenti**, étudiant en cybersécurité à Guardia Cyber School

[LinkedIn](https://www.linkedin.com/in/benjamin-vincenti-835630387) · [TryHackMe](https://tryhackme.com/p/bvincenti) · [GitHub](https://github.com/vbenji23)
