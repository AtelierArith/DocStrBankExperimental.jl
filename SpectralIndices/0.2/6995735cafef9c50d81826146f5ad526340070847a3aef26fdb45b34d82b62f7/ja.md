```
compute_kernel(kernel, params=nothing; kwargs...)
```

指定されたカーネルを、提供されたパラメータまたはキーワード引数を使用して計算します。

# 引数

  * `kernel`: 使用するカーネル関数。`linear`、`poly`、または`RBF`のいずれかである必要があります。
  * `params`: （オプション）カーネル計算のためのパラメータを含む`Dict`、`DataFrame`、または`YAXArray`。
  * `kwargs...`: `params`が提供されていない場合にパラメータに変換されるキーワード引数。

# 戻り値

  * カーネル計算の結果。入力タイプに応じてその型が異なります。

# 例

```julia
result = compute_kernel(linear; params=Dict("a" => 1, "b" => 2))
```
