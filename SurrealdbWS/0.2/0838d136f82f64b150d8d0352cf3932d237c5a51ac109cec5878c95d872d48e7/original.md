````
Surreal(url::String; npool=1)::Surreal

A struct represents a Surreal server.
# Constructors
```julia 
Surreal(url::String)
```
# Keyword arguments
- url: The URL of the Surreal server.
- npool: The number of connection pool. Default is 1.
# Examples
```jldoctest
db = Surreal("ws://localhost:8000/rpc", npool=20)
db = Surreal("http://cloud.surrealdb.com/rpc")
```
````
