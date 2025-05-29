```
struct MCDMSetting
    df::Matrix
    weights::Array{Float64, 1}
    fns::Array{Function, 1}
end

MCDM設定のための不変データ構造。
```

# 引数

  * `df::Matrix`: 行列の型の意思決定行列。
  * `weights::Array{Float64,1}`: 各基準の重みの配列。
  * `fns::Array{<:Function, 1}`: 関数の配列。要素は最小または最大のいずれかです。

# 説明

Topsis、Electre、Waspasなど、多くの手法は、行列とベクトルの型でそれぞれ意思決定行列、重み、および最適化の方向を使用します。MCDMSetting型は、これらの情報を保持し、メソッドに簡単に渡すためのものです。MCDMSettingオブジェクトが作成されると、問題はtopsis(setting)、electre(setting)、waspas(setting)などのいくつかのメソッドに渡すことができます。

# 例

```julia-repl
julia> df = DataFrame();
julia> df[:, :x] = Float64[9, 8, 7];
julia> df[:, :y] = Float64[7, 7, 8];
julia> df[:, :z] = Float64[6, 9, 6];
julia> df[:, :q] = Float64[7, 6, 6];

julia> w = Float64[4, 2, 6, 8];

julia> fns = [maximum, maximum, maximum, maximum];

julia> setting = MCDMSetting(Matrix(df), w, fns)

julia> result = topsis(setting);
julia> # 同じ結果は次のようにして得ることができます
julia> result2 = mcdm(setting, TopsisMethod())
```
