# Semaine 1
## Lundi 01/03
- Présentation des locaux et de l'équipe, réu de lancement, prise en main des ressources informatiques, installations. Dual boot et customization OK.
- Installation UE4 : Sous linux fail car need 100+Go pour la compilaton et la partition home n'a pas été crée à côté de l'espace windows donc flemme de réinstaller linux -> UE4 sous windows (installé à partir de la session mis)
	- La machine sur laquelle je me suis installé ne possède pas de GPU : les ressources du PC sont très limitées quand il est lancé et il y a sans arrêts des crashs de UE4. -> Solutions : l'installer sur pc portable (non), l'installer sur pc fixe mais il faudra le faire venir + attendre le bureau, utiliser une machine avec GPU, quitte à prendre un MAC, voir si on peut le faire travailler sur matrix (à mon avis non)
- Recherche d'articles
- Recherche de tuto UE4

## Mardi 02/03
- Récupération du dépôt Git + prise de contact avec Dao
- Recherche d'ordinateur avec GPU + prise de contact avec Christophe poix
- Exploration du Git
- Construction d'une RoadMap du travail établi
- Recherche d'articles
- Absence aprem car installation internet

## Mercredi 03/03
- Recherche de solutions GPU avec Christophe
- Complétion de la RoadMap du travail établi
- Refonte du README à la racine
- Recherche d'articles / datasets / pistes
- Récupération des modèles

## Jeudi 04/03
- Installation de l'environnement virtuel et des outils de développement
- Point avec Pascal
- Reprise du code

## Vendredi 05/03
- Reprise du code : pb rencontrés
	- Communication avec Dao pour la reprise et correction des certaines choses
- Confirmation que le DenseNet brut fonctionne (sans suprise car reprise du git officiel)
	
# Semaine 2
## Lundi 08/03
- Réunion hebdomadaire
- Reprise du code avec mises à jour Dao
	- DenseDepth : fonctionne mais sensible à la luminosité forte qui peut tromper l'estimation de profondeur. Inquiétant pour la vraie vie.
	- AdapNet : marche mais je n'arrive pas à changer le dossier d'input d'images
- Installation du nouveau GPU : Quadro M6000
	- Pb Epic Games Launcher -> crash par memory leak (sur le PC GPU + le Dell all-in-one)
	
## Mardi 09/03
- Tentative de debuggage du launcher Epic Games (Epic fail)
- Run de seg. sem et depth map sur images réelles
	- Documentation sur les TFRecords
	
## Mercredi 10/03
- Amélioration du script de test d'AdapNet
- Création d'un script de redimensionnement d'images dans un dossier

## Jeudi 11/03
- Création script reshape img from file/folder

## Vendredi 12/03
- Paufinage script reshape
- MàJ du README
- MàJ config linters & testers
- MàJ rapport de stage

# Semaine 3
## Lundi 15/03
- Réunion avec Pascal
- Nettoyage des fichiers AdapNet
- Bataille avec le fonctionnement des modules python
- Problème constaté avec le VPN : impossible d'accéder à des ressources extérieures en fonction de la co
	- Discussion par mail en cours

## Mardi 16/03
- Nettoyage des fichiers AdapNet
- Résolution du problème VPN
- Configuration du planning

## Mercredi 17/03
- Nettoyage des fichiers AdapNet
- Tentatives de résolution du problème GPU
	- 'Réparation' au niveau bios pour le boot.
	- A faire : tenter UE4 sous linux
- Tentatives nouveaux entraînements -> problèmes
	- Prise de contact avec Dao
	
## Jeudi 18/03
- Nettoyage des fichiers AdapNet
- Reprise en profondeur du code dans AdapNet/
- Nettoyage des fichiers Clustering
- Test de gabor.py
- Installation complète d'UE4 sur Ubuntu : OK

## Vendredi 19/03
- Annonce confinement : absence la matinée
- Aprem : 
	- Mise en place de l'accès à distance du poste avec GPU contenant UE4 + accès graphique sur le poste de dev + accès direct via clefs ssh
	- Corrections AdapNet suite à la réponse de Dao
	
# Semaine 4
## Lundi 22/03
- Ajout code et ressources suite à update du git après la réponse de Dao : de nouvelles images (les anciennes dans TrainImages/SS n'étaient pas des labels mais des masques pour la visualisation), du nouveau code pour générer les bons datasets et leurs labels via UnrealCV.
- Tentative installation unrealcv -> bugs
	- Tentative correction manuelle dans code C++ mais échec, projet très gros
- Installation UE4 sur pc fixe perso (lent car pas encore de cable ethernet pour relier à livebox)
- Documentation UE4 & unrealcv

## Mardi 23/03
- Réunion Pascal
- Fixed installation unrealcv en plugin sous UE4 (aucune des branche de build correctement, sur recommandation de Dao j'ai pris les version déjà compilées dans les releases). /!\ Peut-etre d'autres pb de compatibilité avec UE4, à voir inside IDE /!\
	- UnrealCV n'est pas loadé dans UE4 car pb de version (destiné à UE4.16), dit de compiler dans l'IDE mais crash après (?)
- Ré-entrainement à neuf en restaurant le modèle pré-entrainé AdapNet :
	- ré-entrainé avec le ficheir train.py de Dao (y a des formes qui approchent les arbres mais y a encore cet aspect 'points'). En attente du miens 'clean' pour comparer
- Basculement de l'environnement de travail sur le psote à GPU car plus possible d'attendre des années sur le all-in-one. Prend un temps monstrueux à ré-installer conda, aucune idée de pourquoi. En attente.
	- evaluate.py 'clean' confirmé bien marcher comme celui de Dao.

## Mercredi 24/03
- Ré-installation UE4.16 sur fixe appart
- Tentative résolution problème de compatibilité de version unrealcv/UE4.26 sur poste GPU. Si échec -> ré-installation 4.16
- Quelques résultats plus intéressants avec entrainement, attente confirmation Dao + basculement environnement de travail sur poste GPU pour lancer des entraînement plus conséquents
- Basculement de l'environnement de travail sur le poste GPU
	- 1 journée entière + soirée pour faire marcher tensorflow sur le GPU (entre la bonne version de CUDA pour tensorflow-gpu 1.14.0, la création d'un compte pour cuDNN, **le parametrage de gpu_id dans les fichier a passer à 0 (pour set os.environ['CUDA_VISIBLE_DEVICES'] à 0 car single-GPU set)**, la résolution de conflit de versions...
	
## Jeudi 25/03
- Finition transfert environnement de travail :
	- finition paramétrage accès à distance poste GPU au niveau du boot et de la sessions
	- wipe Ubuntu du poste all-in-one.
	- Déménagement du poste dans le coin
- Lecture d'articles

## Vendredi 26/03
- Réunion Pascal
- Lecture d'articles

# Semaine 5
## Lundi 29/03
- Lecture d'articles
- Tentatives de fix Epic Games sur poste GPU
	- Succès : install avant màj du launcher
## Mardi 30/03

- Lecture d'articles
- Recherches config stéréo UE4
	- En fait pas possible nativement, quelques plugins ont l'air d'exister mais pas très connus. 
	- A voir si ce n'est pas plus facile de faire parcourir un chemin à la caméra 2 fois avec des offsets définis
- Entraînement utilisation unrealcv sous UE4 :
	- Pas de GUI, que commande et la plupart crash... peut etre des configs manquantes
- Contact Dao car lien de téléchargement environnement UE4 mort
- Récupération ressources article depth stéréo 360

## Mercredi 31/03
- Tests du code article depth stéréo 360
- Relance Dao
- Réunion Pascal

## Jeudi 01/04
- Récupération environnements :
	- [x] Dao
	- [ ] Guillaume Allibert -> impossible
- Chargement environnements :
	- [ ] Dao
	- [ ] Guillaume Allibert
	
## Vendredi 02/04
- UE4
	- Pas de problème si pas de connexion internet, mais dès qu'on la (re)met : RAM overflow.
	- Fonctionne correctement sous VirtualBox - Win10
- Tentative de résolution bug launcher epic games pour récupérer environnement Guillaume
- Rapport + Récupération info labo auprès de David

# Semaine 6
## Lundi 05/04
- Férié

## Mardi
- Problème majeur sur les distributions à cause d'une mauvaise manipulation des partitions sur Windows : perte d'une grosse demi-journée
- Recherche sur les techniques de synchronisation de caméra
- Import de l'environnement de Dao : viewport complètement noir
- Rapport

## Mercredi 07/04
- Récupération et chargement environnement de Guillaume Allibert sur le fixe à l'appart
- Engagement via Christophe avec les respo réseau pour débloquer l'Epic Games launcher au labo
	- Résolu : désactivation de la détection automatique de sparamètres de proxy auto dans windows...
	- Ré-installation des UE4 16 et 26
- **News sur les présentations : possibilité de tenir un séminaire en mai/juin sur le travail réalisé**
- Séminaire demain jeudi 08/04 9h30 sur la vision (cf. mails)
- Mise en place accès à distance windows
- Recherche sur les techniques de synchronisation de caméra

## Jeudi 08/04
- Séminaire Yufan Kang (University of Tokyo)
- Installation AirSim

## Vendredi 09/04
- Réunion Pascal
- Installation et prise en main du plugin AirSim
	- Tutorials
	- Génération directe d'images equirectangulaires impossible
	- Contrôle du drone impossible au clavier : need une manette compatible suivant cette [liste](https://github.com/Microsoft/AirSim/blob/master/docs/remote_control.md)
	
# Semaine 7
## Lundi 12/04
- AirSim :
	- Tentative de faire fonctionner les API pour prendre des screenshots stereo : échec, dans l'attente de la réponse de Charles Artizzu pour un call Zoom
	- Problème de compréhension de Visual Studio + gestion environnements python sous windows
	- Manque de tutoriels vidéos en ligne

## Mardi 13/04
- Contact Guillaume et Dao. Réunion Guillaume demain 14h + préparation visio
- Airsim :
	- Manipulations et apprentissage.
	- Premières sorties d'image par API
	- 1ère demande s'il y a des manettes ou des télécommandes dans le labo pour controller le drone qui ne peut pas être dirigé au clavier. Peut etre intéressant pour prendre des images perspectives mais pas forcément pour de la stéréo
	- Les APIs sont parfois buggées avec des issues très récentes (ex: les types python non reconnus dans PythonClient/airsim/types.py qu'il faut remplacer par leur int correspondant pour le moment)
	- Peut-être problème avec la seg. sem. si on n'arrive pas à attribuer une couleur différente à chaque arbre individuellement car ce n'est pas le cas par défaut. D'où l'intérêt de garder la solution de Dao sous le coude.
	
- Environnement Dao :
	- Confirmation de corruption de sauvegarde ou en tout cas d'un problème, d'où la prise de contact
	
## Mardi 13/04
	