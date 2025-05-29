```
finufft_makeplan(type::Integer,
                 n_modes_or_dim::Union{Array{Int64},Integer},
                 iflag::Integer,
                 ntrans::Integer,
                 eps::Real;
                 dtype=Float64,
                 kwargs...) -> plan::finufft_plan{dtype}
```

FINUFFTのguruインターフェース用の`finufft_plan`オブジェクトを作成します。タイプは1、2、または3で、与えられたフーリエモードの数を持ちます（タイプ3を除く）。

# 入力

  * `type`            変換タイプ: 1, 2, または 3
  * `n_modes_or_dim`  `type`が1または2の場合、各次元のフーリエモードの数: 1Dでは`ms`、2Dでは`[ms mt]`、3Dでは`[ms mt mu]`。 したがって、その長さが次元を設定し、1、2、または3でなければなりません。 `type`が3の場合、対照的にその*値*が次元を固定します。
  * `iflag`   >=0の場合、指数に+符号を使用し、それ以外の場合は-符号を使用します。
  * `ntrans`          同時に計算する変換の数
  * `eps`     要求される相対精度（一般的に1e-15から1e-1の間）、実数で、`dtype`の型と一致する必要はありません
  * `dtype`           `Float32`または`Float64`、単精度または倍精度のプラン
  * `kwargs`  （オプション）: オプションについては、`nufft_opts`およびhttps://finufft.readthedocs.io/en/latest/opts.htmlを参照してください

# 戻り値

  * finufft_plan構造体

# 例

```julia-repl
julia> p = finufft_makeplan(2,10,+1,1,1e-6);
```

10個のフーリエモードと許容誤差1e-6を持つ1Dタイプ2のFloat64変換のプランを作成します。

```julia-repl
julia> p = finufft_makeplan(1,[10 20],+1,1,1e-6);
```

10*20のフーリエモードを持つ2Dタイプ1のFloat64変換のプランを作成します。

```julia-repl
julia> p = finufft_makeplan(3,2,+1,1,1e-4,dtype=Float32,nthreads=4);
```

許容誤差1e-4を持つ2Dタイプ3のFloat32変換のプランを作成し、4スレッドを使用します。
