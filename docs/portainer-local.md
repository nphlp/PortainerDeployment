# Portainer Local Installation

### Installation

-   [ ] Cloner ce repo

-   [ ] Copier le `.env.example` en `.env` et adapter les variables d'environnement

```bash
cp .env.example .env
nano .env
```

-   [ ] Générer des certificats SSL et Let's Encrypt locaux auto-signés

```bash
make tls
```

-   [ ] Mapper les domaines au localhost dans le fichier `/etc/hosts`

```bash
# Editer le fichier hosts
nano /etc/hosts

# Inserer les lignes suivantes
127.0.0.1 preview.local.dev
127.0.0.1 front.local.dev
127.0.0.1 traefik.local.dev
127.0.0.1 edge.local.dev
127.0.0.1 portainer.local.dev
```

### Lancer Portainer

-   [ ] Lancer la stack Portainer/Traefik

```bash
make portainer-local
```

-   [ ] Accéder à l'interface Portainer via : [https://portainer.local.dev](https://portainer.local.dev)

### Arrêter Portainer

```bash
make portainer-local-stop
```

## Lancer une application Next.js dans Portainer

### Via Portainer UI

Cette méthode permet à Portainer de tracker le repo Git, les fonctionnalités de Portainer sont toutes disponibles.

- [ ] Lancer Portainer en local avec `make portainer`
- [ ] Accéder à l'interface Portainer via : [https://portainer.local.dev](https://portainer.local.dev)
- [ ] Sélectionner l'environnement `primary`
- [ ] Aller dans `Stacks` -> `Add stack`
- [ ] Nommer la stack `nextjs-example`
- [ ] Ajouter un repository Git `https://github.com/mon-compte/mon-repo.git`
- [ ] Choisir la référence cible `refs/heads/main`
- [ ] Choisir le `compose.yml` cible
- [ ] Ajouter les variables d'environnement
- [ ] Déployer

### Via CLI

Cette méthode ne permet pas à Portainer de tracker le repo Git, les fonctionnalités de Portainer sont limitées.

- [ ] Se rendre dans le dossier du projet à déployer (ex: `~/Code/NextjsDeploy/`)
- [ ] Lancer la stack en local avec `make local`
- [ ] Accéder à l'interface Portainer via : [https://portainer.local.dev](https://portainer.local.dev)
- [ ] Visualiser la stack dans l'environnement `primary`
- [ ] Arrêter la stack en local avec `make local-stop`
