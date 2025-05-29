`ParameterTable`は構造方程式モデルの仕様を含みます。

# コンストラクタ

```
(1) ParameterTable(graph; observed_vars, latent_vars, ...)

(2) ParameterTable(ram_matrices; ...)
```

(1) グラフまたは (2) RAM行列から構築された`ParameterTable`を返します。

# 引数

  * `graph`: `@StenoGraph`を介して定義されたグラフ
  * `observed_vars::Vector{Symbol}`: 観測変数名
  * `latent_vars::Vector{Symbol}`: 潜在変数名
  * `ram_matrices::RAMMatrices`: `RAMMatrices`オブジェクト

# 例

[モデル仕様](@ref)および[グラフインターフェース](@ref)に関するオンラインドキュメントを参照してください。

# 拡張ヘルプ

## 追加のキーワード引数

  * `parname::Symbol = :θ`: 自動生成されたパラメータラベルのプレフィックス
