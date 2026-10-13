# P11 Produisez une étude de marché avec Python

L'entreprise est fictive. Les données viennent de sources publiques (FAO et Banque mondiale).

## Contexte

La poule qui chante est une entreprise française d'agroalimentaire qui élève et vend des poulets sous le label Agriculture Biologique. Son activité est aujourd'hui uniquement française et le PDG souhaite évaluer une expansion à l'international, sans pays ni continent imposé au départ. J'ai rassemblé et nettoyé des données de plusieurs sources, puis utilisé une ACP et deux méthodes de clustering pour regrouper les pays et recommander ceux à approfondir.

## Objectifs

* Constituer un jeu de données propre avec au moins 100 pays, couvrant au moins 60 % de la population mondiale, et au moins 8 variables
* Choisir des variables complémentaires aux données de la FAO grâce à la grille PESTEL
* Réduire les dimensions avec une ACP et analyser le cercle des corrélations
* Regrouper les pays avec une CAH puis un K-means, et comparer les deux résultats
* Recommander des pays cibles et présenter la démarche à un public non technique

## Réalisations

* Nettoyage et fusion de 7 fichiers (2 fichiers FAO, 3 indicateurs de la Banque mondiale, coordonnées des capitales et table des codes ISO)
* Extraction de la viande de volaille parmi 98 produits FAO, puis passage du format long au format large pour obtenir une ligne par pays
* Détection et suppression de 265 doublons dans le fichier de stabilité politique
* Harmonisation des noms de pays entre les sources avec un dictionnaire de 16 corrections
* Fusion de la distance à la France par code ISO, car les noms de pays étaient en anglais, et correction de la Namibie dont le code "NA" était lu comme une valeur manquante
* Jeu de données final de 163 pays et 8 variables, plus la distance à la France gardée comme variable annexe
* Standardisation des variables puis ACP, avec cercle des corrélations et projection des pays
* Repérage de 4 pays aux profils extrêmes, écartés du clustering pour ne pas fausser les groupes
* CAH (dendrogramme, 5 groupes) puis K-means (méthode du coude et score de silhouette), avec comparaison des deux résultats
* Construction d'un score pour départager les pays du cluster cible, ajusté ensuite par la distance à la France
* Support de présentation pour le COMEX avec recommandations de pays

## Résultats clés

* 163 pays retenus, soit 95,95 % de la population mondiale
* Les deux premiers axes de l'ACP résument 60 % de l'information
* La CAH et le K-means aboutissent à des groupes très proches
* Un cluster de 36 pays se détache avec un fort pouvoir d'achat, une bonne stabilité politique et un marché pas encore saturé
* Le Luxembourg arrive en tête, suivi de l'Islande, du Danemark, de l'Irlande et de la Suisse
* Sans la distance, le Koweït et le Canada entraient dans le top 5, ce qui montre l'intérêt de l'intégrer au score

## Outils

Python, pandas, NumPy, scikit-learn, SciPy, Matplotlib, Seaborn, geopy, Google Colab

## Compétences

* Collecter, nettoyer et fusionner des données issues de sources et de formats différents
* Harmoniser des noms de pays et gérer les doublons et valeurs manquantes
* Choisir des variables pertinentes avec la grille PESTEL
* Réaliser une ACP et interpréter le cercle des corrélations
* Appliquer et comparer une CAH et un K-means
* Construire un score de décision et justifier ses choix
* Restituer une analyse à un public non technique

## Fichiers

* `notebook_1_preparation_nettoyage_analyse_exploratoire.ipynb` notebook de préparation et de nettoyage des données
* `notebook_2_clustering_visualisations` notebook de l'ACP, du clustering et des visualisations
