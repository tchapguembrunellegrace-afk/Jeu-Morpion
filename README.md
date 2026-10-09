# Jeu-Morpion
        Projet de programmation structurée - Jeu Morpion
PROJET : JEU MORPION
Matière : Programmation structurée
Nom du projet : Développement du jeu Morpion
Langage de programmation : langage C
Année académique : 2026-2027

1. Présentation du projet
   
Le projet consiste à concevoir et à développer un jeu Morpion en utilisant les principes de la programmation structurée.
L'objectif est de mettre en pratique les connaissances acquises en algorithmique et en programmation, notamment les variables, les conditions, les boucles, les tableaux et les fonctions ou procédures.
Le jeu permettra à deux joueurs de s'affronter sur une grille de 3 lignes et 3 colonnes.

## 2. Liste des membres du groupe

-TCHANGUEM TEMEBE BRUNELLE GRACE gl2

-AMOMBO MBIDA CHRISTIANE gl2

-AFAGA LEO SEBASTIANO gl2


## 3. Description du jeu

Le Morpion est un jeu de réflexion qui oppose deux joueurs sur une grille carrée composée de neuf cases.
Le premier joueur utilise le symbole X, tandis que le deuxième utilise le symbole O.
Les joueurs placent leurs symboles à tour de rôle dans les cases libres. Le but est d'aligner trois symboles identiques horizontalement, verticalement ou diagonalement.
La partie se termine lorsqu'un joueur gagne ou lorsque toutes les cases sont occupées sans qu'aucun joueur ne gagne.

## 4. Règles du jeu

Les règles du jeu sont les suivantes :

1.	Le jeu commence avec une grille vide de 3 × 3. 
2.	Deux joueurs participent à la partie. 
3.	Le joueur 1 utilise le symbole X. 
4.	Le joueur 2 utilise le symbole O. 
5.	Les joueurs jouent à tour de rôle. 
6.	Chaque joueur doit choisir une case libre. 
7.	Il est interdit de jouer dans une case déjà occupée. 
8.	Un joueur gagne lorsqu'il aligne trois symboles identiques sur une ligne, une colonne ou une diagonale. 
9.	Si toutes les cases sont occupées sans victoire, la partie se termine par un match nul. 
10.	Une nouvelle partie peut être lancée après la fin de la précédente.

## 5. Les étapes de réalisation du projet

Pour mener à bien le projet de développement du jeu de Morpion, nous suivrons plusieurs étapes, depuis l'analyse du sujet jusqu'à la livraison finale du programme. Chaque étape permettra d'organiser le travail, de respecter les objectifs fixés et de garantir le bon fonctionnement du jeu.

5.1. Analyse du sujet

Durée estimée : 1 jour

Comprendre le fonctionnement du jeu de Morpion et identifier les objectifs du projet.

5.2. Rédaction des règles

Durée estimée : 1 jour

Définir les règles du jeu ainsi que les conditions de victoire, de défaite et de match nul.

5.3. Élaboration du cahier des charges

Durée estimée : 1 jour

Déterminer les fonctionnalités attendues et les contraintes à respecter lors de la réalisation du projet.

5.4. Conception de l'algorithme

Durée estimée : 2 jours

Élaborer le pseudo-code décrivant les différentes étapes du fonctionnement du jeu.

5.5. Réalisation de l'organigramme

Durée estimée : 1 jour

Représenter graphiquement les différentes étapes du jeu afin de faciliter la compréhension de son fonctionnement.

5.6. Préparation du programme

Durée estimée : 1 jour

Définir les variables nécessaires et préparer la structure de la grille de jeu.

5.7. Programmation

Durée estimée : 3 jours

Développer les différentes fonctionnalités du jeu conformément aux spécifications définies dans le cahier des charges.

5.8. Détection des conditions de victoire

Durée estimée : 1 jour

Mettre en place un mécanisme permettant de vérifier les lignes, les colonnes et les diagonales afin de déterminer si un joueur a gagné.

5.9. Tests du programme

Durée estimée : 2 jours

Tester plusieurs situations de jeu pour vérifier le bon fonctionnement des différentes fonctionnalités et s'assurer que les règles sont correctement appliquées.

5.10. Correction des erreurs

Durée estimée : 1 jour

Identifier et corriger les erreurs détectées pendant les tests afin d'améliorer la fiabilité du programme.

5.11. Rédaction de la documentation

Durée estimée : 2 jours

Rassembler les documents nécessaires et expliquer le fonctionnement du programme, son organisation et ses principales fonctionnalités.

5.12. Préparation de la présentation

Durée estimée : 1 jour

Préparer la démonstration du jeu et présenter les principales fonctionnalités développées.

5.13. Livraison finale

Durée estimée : 1 jour

Effectuer une dernière vérification du projet, s'assurer que tous les éléments sont présents et procéder à la livraison finale.

5.14. Durée totale du projet

La durée totale estimée pour la réalisation du projet est de 19 jours, en considérant que les différentes étapes sont effectuées successivement et que les durées prévues sont respectées.

5.15. Résultat attendu

À la fin de ces différentes étapes, nous disposerons d'un jeu de Morpion fonctionnel, respectant les règles définies dans le cahier des charges. Le programme permettra aux joueurs de participer à une partie, de vérifier automatiquement les conditions de victoire et de détecter les situations de match nul.

Des tests permettront de vérifier le bon fonctionnement du jeu. Enfin, la documentation et la présentation faciliteront la compréhension du projet et de son fonctionnement.

6. code source

#include <stdio.h>

char g[3][3];

void init() {
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            g[i][j] = ' ';
}

void afficher() {
    printf("\n");
    for (int i = 0; i < 3; i++) {
        printf(" %c | %c | %c \n", g[i][0], g[i][1], g[i][2]);
        if (i < 2) printf("---+---+---\n");
    }
    printf("\n");
}

int gagne(char c) {
    for (int i = 0; i < 3; i++) {
        if (g[i][0]==c && g[i][1]==c && g[i][2]==c) return 1;
        if (g[0][i]==c && g[1][i]==c && g[2][i]==c) return 1;
    }
    if (g[0][0]==c && g[1][1]==c && g[2][2]==c) return 1;
    if (g[0][2]==c && g[1][1]==c && g[2][0]==c) return 1;
    return 0;
}

int main() {
    char joueur = 'X';
    int l, c, tours = 0;
    init();
    while (tours < 9) {
        afficher();
        printf("Joueur %c (ligne colonne, 1-3) : ", joueur);
        if (scanf("%d %d", &l, &c) != 2) break;
        l--; c--;
        if (l < 0 || l > 2 || c < 0 || c > 2 || g[l][c] != ' ') {
            printf("Case invalide !\n");
            continue;
        }
        g[l][c] = joueur;
        tours++;
        if (gagne(joueur)) {
            afficher();
            printf("Le joueur %c gagne !\n", joueur);
            return 0;
        }
        joueur = (joueur == 'X') ? 'O' : 'X';
    }
    afficher();
    printf("Match nul !\n");
    return 0;
}

