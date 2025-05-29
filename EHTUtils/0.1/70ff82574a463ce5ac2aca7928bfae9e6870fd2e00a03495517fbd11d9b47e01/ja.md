```
unique_ids(itr, sort::Bool=true; keywords...)
```

これは、入力のユニークな要素のベクトルだけでなく、逆インデックスのベクトルも返す`unique`関数のバリアントです。

# 引数

  * `itr`: イテラブル
  * `sort::Bool`: 出力ベクトルがソートされているかどうか。デフォルトは`true`。
  * `keywords...`: `sort == true`のときに考慮される`permsort`関数のキーワード。

# 例

```julia
# 元のベクトル
vec = [1,1,3,4,2,3,1,4]

# ユニークな要素と逆インデックスを取得
uvec, idx = unique_ids(vec) # uvecは[1,3,4,2]であるべき

# これにより元のベクトルが再構築される
rec = uvec[idx]
println(rec == vec)
```
