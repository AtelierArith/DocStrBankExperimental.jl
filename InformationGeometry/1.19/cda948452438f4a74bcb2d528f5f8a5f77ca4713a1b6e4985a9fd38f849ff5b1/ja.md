```
UnknownVarianceDataSet(x::AbstractVector, y::AbstractVector, σ_x⁻¹::Function, σ_y⁻¹::Function, cx::AbstractVector, cy::AbstractVector; BesselCorrection::Bool=false)
UnknownVarianceDataSet(x::AbstractVector, y::AbstractVector, dims::Tuple{Int,Int,Int}, σ_x⁻¹::Function, σ_y⁻¹::Function, cx::AbstractVector, cy::AbstractVector, errorparamsplitter::Function; BesselCorrection::Bool=false)
```

`UnknownVarianceDataSet`型は、分散の大きさが事前に不明であるが、誤差が`σ(x, y_pred, c)`の形の誤差モデルを介して指定されるデータをエンコードします。ここで、`c`は誤差パラメータのベクトルです。このパラメータ化された誤差モデルは、その後、観測値`y`の標準偏差を推定するために使用されます。

!!! note
    パフォーマンスを向上させるために、実装では*逆*誤差モデル、すなわち関数`σ⁻¹(x, y_pred, c)`の指定が実際に必要です。`ydim`が1より大きい場合、逆誤差モデルは行列を出力する必要があり、すなわち共分散`Σ`のコレスキー分解`S`であり、`Σ == S' * S`となります。


`UnknownVarianceDataSet`を構築するには、独立変数のベクトル`x`、従属変数のベクトル`y`、逆誤差モデル`σ⁻¹(x, y_pred, c)`、および誤差パラメータのベクトル`c`の初期推定を指定する必要があります。オプションで、`θ -> (modelparams, xerrorparams, yerrorparams)`の形の明示的な`errorparamsplitter`関数を指定することができ、これによりパラメータがモデルパラメータのタプルと、逆誤差モデル`σ⁻¹`にのみ渡される誤差パラメータに分割されます。

!!! warn
    外部に見えるパラメータは、モデルに転送される前に`errorparamsplitter`によって最初に処理されます。ここで、`modelparams`は埋め込み変換によってさらに修正される可能性があります。


# 例:

最も単純なケースでは、すべてのデータポイントが相互に独立しており、それぞれが単一の$x$成分と単一の$y$成分を持つ場合、4つのポイントからなる`DataSet`は次のように構築できます。

```julia
DS = UnknownVarianceDataSet([1,2,3,4], [4,5,6.5,7.8], (x,y,cx)->1/exp10(cx[1]), (x,y,cy)->1/exp10(cy[1]), [0.25], [0.8])
```

!!! note
    誤差パラメータは、ガウス尤度の正規化項において`log(c)`に比例してペナルティが課されるため、一般的に指数化することが推奨されます。最大尤度推定量がバイアスされることを考慮して、逆誤差に対してBessel補正`sqrt((length(xdata(DS))+length(ydata(DS))-length(params))/(length(xdata(DS))+length(ydata(DS))))`を適用することができます。


```
