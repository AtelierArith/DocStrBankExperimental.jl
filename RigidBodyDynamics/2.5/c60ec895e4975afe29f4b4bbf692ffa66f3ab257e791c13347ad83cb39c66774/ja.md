```julia
mutable struct Mechanism{T}
```

`Mechanism`は剛体とジョイントの相互接続を表します。`Mechanism`はジョイントのレイアウトと慣性パラメータを格納しますが、状態依存の情報は格納しません。
