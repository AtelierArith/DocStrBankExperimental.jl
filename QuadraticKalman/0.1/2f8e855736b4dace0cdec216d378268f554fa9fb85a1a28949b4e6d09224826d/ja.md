```
model_to_params(model::QKModel{T, T2}) where {T<:Real, T2}
```

QKModelオブジェクトを制約のないパラメータのベクトルに変換します。

パラメータの順序は次のとおりです。

1. **状態パラメータ:**

      * `mu` (長さ N)
      * `Phi` (N×N, 列優先で格納)
      * 状態ノイズスケーリングファクターΩのための制約のないパラメータ: 各行 `i = 1,...,N` と列 `j = 1,...,i` に対して（すなわち下三角部分）:

          * `i == j` の場合: パラメータは `log(Ω[i,i])`
          * それ以外: パラメータは `Ω[i,j]`
2. **測定パラメータ:**

      * `A` (長さ M)
      * `B` (M×N, 列優先で格納)
      * `C` (M個の行列のベクトル; 各行列はN×Nで、列優先でフラット化される)
      * 測定ノイズスケーリングファクターDのための制約のないパラメータ: 各行 `i = 1,...,M` と列 `j = 1,...,i` に対して:

          * `i == j` の場合: パラメータは `log(D[i,i])`
          * それ以外: パラメータは `D[i,j]`
      * `alpha` (M×M, 列優先で格納)

# 戻り値

`params_to_model`に渡すと元のQKModelを再構築する制約のないパラメータのベクトル。
