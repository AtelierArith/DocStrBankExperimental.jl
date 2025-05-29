````
Surreal(url::String; npool=1)::Surreal

サーバーを表す構造体です。
# コンストラクタ
```julia 
Surreal(url::String)
```
# キーワード引数
- url: SurrealサーバーのURL。
- npool: 接続プールの数。デフォルトは1です。
# 例
```jldoctest
db = Surreal("ws://localhost:8000/rpc", npool=20)
db = Surreal("http://cloud.surrealdb.com/rpc")
```
````
