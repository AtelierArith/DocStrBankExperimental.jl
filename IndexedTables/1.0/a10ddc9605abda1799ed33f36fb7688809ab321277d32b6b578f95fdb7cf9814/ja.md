```
ndsparse(keys, values; kw...)
```

与えられた `keys` と `values` 列を使って NDSparse 配列を構築します。構築時に、キーとデータは `keys` の辞書順でソートされます。

# キーワード引数オプション:

  * `agg = nothing` – 重複するキーの値を集約する関数。
  * `presorted = false` – キー列はすでにソートされていますか？
  * `copy = true` – `keys` と `values` の列をコピーするべきですか？
  * `chunks = nothing` – データを `chunks` チャンクに分配するための整数を提供します。

      * 良い選択肢は `nworkers()` です（`using Distributed` の後）
      * 参照: [`distribute`](@ref)

# 例:

```
x = ndsparse(["a","b"], [3,4])
keys(x)
values(x)
x["a"]

# 列の名前付きタプルで構築された場合、次元に名前が付けられます
x = ndsparse((index = 1:10,), rand(10))
x[1]

# 列の（名前付き）タプルを渡すことで複数の次元を持つ
x = ndsparse((x = 1:10, y = 1:2:20), rand(10))
x[1, 1]

# 値の列も名前付きタプルを介して名前を持つことができます
x = ndsparse(1:10, (x=rand(10), y=rand(10)))
```
