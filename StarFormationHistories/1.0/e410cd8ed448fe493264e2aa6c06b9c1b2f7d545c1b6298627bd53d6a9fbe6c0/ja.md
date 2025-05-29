```
result::StatsBase.Histogram =
    partial_cmd(m_ini::AbstractVector{<:Number},
                colors::AbstractVector{<:Number},
                mags::AbstractVector{<:Number},
                imf;
                dmod::Number=0,
                normalize_value::Number=1,
                mean_mass::Number=mean(imf),
                edges=nothing,
                xlim=extrema(colors),
                ylim=extrema(mags),
                nbins=nothing,
                xwidth=nothing,
                ywidth=nothing)
```

星のヘス図を作成します。これは、x軸に光度 `colors`、y軸に光度マグニチュード `mags`、初期質量 `m_ini` を持つ等時線からのエラーのないものです。これは光度誤差によって平滑化されていないため、一般的には有用ではありませんが、比較チェックのために提供されています。ほとんどの引数は [`bin_cmd`](@ref) と同様です。唯一のユニークなキーワード引数は、ヘス図で望む有効な星の質量を与える乗法因子である `normalize_value::Number` と、提供された初期質量関数 `imf` によって示される平均星質量である `mean_mass::Number` です。
