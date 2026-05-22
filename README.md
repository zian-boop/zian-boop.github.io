# Wall Is You - Projet de programmation

## Description
Ce projet c'est une adaptation du jeu de réflexion "Wall Is You" réalisée dans le cadre du BUT Informatique 1 (SAE « Initiation au développement »). Le but est de faire pivoter les salles d'un donjon afin de guider un aventurier vers les dragons qui l'occupent.

## Equipe
Ce travail a été réalisé en binôme par BHATT Piyush et XU Zian, du groupe TDA_alpha_sae_5.

## Installation et lancement
Le projet est organisé de manière modulaire :
- main.py : point d'entrée, gère le menu, la boucle de jeu et orchestre les modules.
- moteur.py : implémente la logique du jeu (rotation des salles, connexions, combats).
- interface.py : gère l'affichage avec la bibliothèque fournie fltk.
- donjons_data.py : contient les donjons prédéfinis (grilles et positions des personnages).
- intention_manuelle.py : convertit les clics de la souris en positions et construit l'intention de déplacement.
- dragons_mobiles.py : variante où les dragons se déplacent de façon aléatoire après le tour de l'aventurier.
- fltk.py : bibliothèque graphique fournie.
- Tests_validation.py : script de tests pour vérifier le bon fonctionnement du moteur et la présence des fichiers.
- Le dossier images/ contient les sprites nécessaires (salles, aventurier et dragons) utilisés par l'interface.

### Prérequis
- Python 3.8 ou supérieur
- Module `fltk` (fourni avec le projet)

## Organisation du dépôt

### Lancer le jeu
```bash
python3 main.py
```

### Lancer les tests
```bash
python3 Tests_validation.py
```

## Contrôles du jeu

- **Clic gauche** : Faire pivoter une salle de 90°
- **Clic droit** : Tracer l'intention de déplacement de l'aventurier
- **Espace** : valider l'intention et lancer le tour de l'aventurier
- **R** : Recommencer le niveau
- **C** : Effacer le chemin tracé
- **Échap** : Retour au menu

## Structure du projet

```
wall-is-you/
├── images/               # Images des salles et personnages
├── donjons_data.py      # Données des donjons
├── interface.py         # Interface graphique (fltk)
├── moteur.py            # Logique du jeu
├── intention_manuelle.py # Gestion du tracé manuel
├── dragons_mobiles.py   # Variante : dragons mobiles
├── main.py              # Point d'entrée
├── fltk.py              # Module graphique
└── Tests_validation.py  # Tests
```

## Images nécessaires

Le jeu nécessite les fichiers images suivants dans le dossier `images/` :

### Personnages
- `aventurier.png`
- `dragon.png`

### Salles avec rotations
- `salle_croix_0.png` (salle symétrique)
- `salle_t_0.png`, `salle_t_90.png`, `salle_t_180.png`, `salle_t_270.png`
- `salle_l_0.png`, `salle_l_90.png`, `salle_l_180.png`, `salle_l_270.png`
- `salle_ligne_0.png`, `salle_ligne_90.png`

**Note :** Si une image manque, le jeu affiche un rectangle gris à la place.

## Structure de données

### Salle
Chaque salle est un tuple de 4 booléens : `(haut, droite, bas, gauche)`

Exemple :
```python
salle = (True, True, False, False)  # Passages en haut et à droite
```

### Donjon
Liste de listes de salles :
```python
donjon = [
    [(False, True, False, False), (False, False, True, True)],
    [(True, False, False, False), (True, False, False, True)],
]
```

### Personnages
- Aventurier : `[(ligne, colonne), niveau]`
- Dragons : Liste de `[(ligne, colonne), niveau]`

## Fonctionnalités implémentées

### Tâche 1 : Moteur de jeu ✓
- Représentation des salles et du donjon
- Rotation des salles
- Vérification des connexions
- Gestion des combats
- Déplacement de l'aventurier

### Tâche 2 : Interface graphique ✓
- Menu de sélection des donjons
- Affichage de la grille avec images
- Affichage des personnages
- Tracé manuel de l'intention
- Messages de victoire/défaite

### Variante : Dragons mobiles ✓
- Les dragons se déplacent aléatoirement après chaque tour
- Gestion des collisions entre dragons

## Choix techniques

Les salles sont représentées par des tuples de quatre booléens (haut, droite, bas, gauche) ; un donjon est une liste de listes de ces salles. L'aventurier et les dragons sont stockés sous la forme [(ligne, colonne), niveau]. La logique du jeu est séparée de l'interface afin de respecter le principe de modularité. Le code n'utilise que des notions vues en première année et ne fait appel à aucun module externe.