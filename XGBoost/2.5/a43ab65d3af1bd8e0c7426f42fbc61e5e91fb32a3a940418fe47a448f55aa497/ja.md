```
DMatrix <: AbstractMatrix{Union{Missing,Float32}}
```

xgboost [`Booster`](@ref) によって理解されるデータを格納するためのデータ構造です。これらは特徴とターゲットの両方を格納できます。 `DMatrix` の値には他の `AbstractMatrix` と同様にアクセスできますが、その際に追加のアロケーションが発生します。パフォーマンスの良いインデクシングや行列操作のコードは、直接 `DMatrix` を使用すべきではありません。

主な配列の他に、`DMatrix` オブジェクトにはさまざまな「情報」フィールドが関連付けられることがあります。トレーニングターゲット変数は、`label` という名前の特別な情報フィールドに格納されます。詳細は [`setinfo!`](@ref) および [`setinfos!`](@ref) を参照してください。これらは [`getinfo`](@ref) および [`getlabel`](@ref) を使用して取得できます。

xgboost ライブラリは内部的にすべてのデータを `Float32` で表現するため、入力データはこの形式で提供されない限り自動的にコピーされます。残念ながら、C と Julia で使用される異なる表現のため、`Transpose` でない任意の行列もコピーされます。

### `missing` 値について

Xgboost は `missing` データでのトレーニングをサポートしています。そのようなデータは単にツリーの分割から省略されます。`DMatrix` は内部的に `Float32` 行列であるため、`libxgboost` は欠損値を表すために設定可能なデフォルト値を使用します。詳細は以下の `missing_value` キーワード引数を参照してください（デフォルトは `NaN32`）。この値は行列の構築時にのみ使用されます。これにより、入力行列の要素は最終的に `missing` に変換されます。最も明白な結果は、`NaN32` 値がデフォルト引数で自動的に `missing` に変換されることです。提供されたコンストラクタは、`missing` 値が保持されることを保証します。

要約: `DMatrix` は `missing` をサポートし、`NaN` は `missing` に変換されます。

## コンストラクタ

```julia
DMatrix(X::AbstractMatrix; kw...)
DMatrix(X::AbstractMatrix, y::AbstractVector; kw...)
DMatrix((X, y); kw...)
DMatrix(tbl; kw...)
DMatrix(tbl, y; kw...)
DMatrix(tbl, yname::Symbol; kw...)
```

## 引数

  * `X`: `DMatrix` にラップされた主なデータである行列。要素は `missing` である可能性があります。 `Float32` 要素を持つ行列はコピーする必要はありません。
  * `y`: `label` 情報フィールドに割り当てるデータ。これはトレーニングに使用されるターゲット変数です。 `label` キーワードで設定することもできます。
  * `tbl`: 表形式の入力行列。 `tbl` は Tables.jl インターフェースを満たす必要があります。表形式でデータが渡されると、特徴名は自動的に設定されますが、キーワード引数で上書きすることもできます。
  * `yname`: 表形式の引数 `tbl` が渡された場合、`yname` はラベルデータを保持する列の名前です。これは自動的に特徴から省略されます。

### キーワード引数

  * `missing_value`: `missing` として解釈される入力データの要素の `Float32` 値。デフォルトは `NaN32` です。
  * `label`: トレーニングターゲットデータ。これは上記の `y` 引数と同じです。すなわち、`DMatrix(X,y)` と `DMatrix(X, label=y)` は同等です。
  * `weight`: 各データポイントの重みの `AbstractVector`。この配列は主データ行列の行数と同じ長さでなければなりません。
  * `base_margin`: このデータセットでトレーニングされたブーストモデルのグローバルバイアスを設定します。詳細は https://xgboost.readthedocs.io/en/stable/prediction.html#base-margin を参照してください。

## 例

```julia
(X, y) = (randn(10,3), randn(10))

# 以下はすべて同等です
DMatrix(X, y)
DMatrix((X, y))
DMatrix(X, label=y)

DMatrix(X, y, feature_names=["a", "b", "c"])  # 特徴名を明示的に設定

df = DataFrame(A=randn(10), B=randn(10))
DMatrix(df)  # 特徴名 ["A", "B"] はありますが、ラベルはありません
```
