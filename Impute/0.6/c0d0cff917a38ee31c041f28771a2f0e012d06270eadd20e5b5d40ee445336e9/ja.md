```
impute(data::T, imp; kwargs...) -> T
```

欠損データをインプテータ `imp` によって補完した新しいコピーの `data` を返します。行列やテーブルの場合、データは1つの変数/列ずつ補完されます。これが望ましい動作でない場合は、このメソッドをオーバーロードするか、異なる `dims` 値を指定する必要があります。

# 引数

  * `data`: 補完するデータ
  * `imp::Imputor`: 使用するインプテータメソッド

# 戻り値

  * 値が補完された入力 `data`

# 例

```jldoctest
julia> using Impute: Interpolate, impute

julia> v = [1.0, 2.0, missing, missing, 5.0]
5-element Vector{Union{Missing, Float64}}:
 1.0
 2.0
  missing
  missing
 5.0

julia> impute(v, Interpolate())
5-element Vector{Union{Missing, Float64}}:
 1.0
 2.0
 3.0
 4.0
 5.0
```
