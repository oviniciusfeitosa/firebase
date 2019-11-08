# Firebase

O Firebase é uma plataforma de desenvolvimento de aplicativos para dispositivos móveis e web desenvolvida pela Firebase, Inc. em 2011 e adquirida pelo Google em 2014. Mais informaçõoes [aqui](https://en.wikipedia.org/wiki/Firebase).

## Database

Os nós são acessados através de uma referência `ref`

## Gravação

Para definir dados, utilize o método `set`.

```console
function writeUserData(userId, name, email, imageUrl) {
    firebase.database().ref('users/' + userId).set({
        username: name,
        email: email,
        profile_picture : imageUrl
    });
}
```

## Leitura

Os dados podem ser obtidos da seguinte maneira.

```console
var userId = firebase.auth().currentUser.uid;
return firebase.database().ref('/users/' + userId).once('value').then(function(snapshot) {
    var username = (snapshot.val() && snapshot.val().username) ||  'Visitante';
    // ...
});
```

## Remoção

Basicamente os nós são acessados através de uma referência `ref`.

```console
firebase.database().ref('/users/' + userId).remove();
firebase.database().ref.child(key).remove();
```

Outra opção é acessar a referência diretamente de subgrupos.
```console
var grupo2 = firebase.database().ref('grupo1/grupo2');
grupo2.remove() .then(function() {
    console.log("Remoção concluída");
  }) .catch(function(error) {
    console.log("Falha ao remover: " + error.message);
});
```

## Referências
- [Referência 1](https://firebase.google.com/docs/database/web/read-and-write)
