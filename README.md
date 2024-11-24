# Crud-Application-by-Node-Express-and-MongoDB


## Get USer information by form/ Client side

app.jsx
```js
function App() {

  const handleAddUser = event => {
    event.preventDefault()
    const form = event.target;
    const name = form.name.value;
    const email = form.email.value;
    const user = {name, email}
    console.log(user);
  }

  return (
    <>
      <h2>Crud Application</h2>
      <form onSubmit={handleAddUser}>
        <input type="text" name='name' />
        <input type="email" name='email' />
        <input type="submit" value='Add User' />
      </form>
      
    </>
  )
}

export default App

```

## Send User Information in Backend Database/ ServerSide

index.js
```js
    app.post('/users', async(req, res) => {
        const user = req.body;
        console.log(`New User: `, user);
    })

```

## Fetch data from server side url (Ex: localhost:5000/user) / Client Side

app.jsx
```js
    const handleAddUser = event => {
        // event.preventDefault()
        // const form = event.target;
        // const name = form.name.value;
        // const email = form.email.value;
        // const user = {name, email}
        // console.log(user);

        fetch('http://localhost:5000/users', {
        method: 'POST',
        headers: {
            'content-type': 'application/json'
        },
        body: JSON.stringify(user)
        })
        .then(res => res.json())
        .then(data => {
        console.log(data)
        })
    }

```

## Send data in database by using Node MondoDB Crud website insert documentation following

index.js
```js
    // await client.connect();

    // from  node mongodb crud website
    const database = client.db("userDB");
    const usersCollection = database.collection("users");

    app.post('/users', async(req, res) => {
        // const user = req.body;
        // console.log(`New User: `, user);
        const result = await usersCollection.insertOne(user);
        res.send(result)
    })

```


