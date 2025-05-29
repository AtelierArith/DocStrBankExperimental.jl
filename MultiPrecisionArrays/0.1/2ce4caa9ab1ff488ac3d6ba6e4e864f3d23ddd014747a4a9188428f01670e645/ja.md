mpglu(A::AbstractArray{TW,2}; TF=Float32, TR=nothing,      residterm=residtermdefault1, basissize=10) where TW <: Real

多倍精度GMRES対応配列のコンストラクタと因子分解を組み合わせます。

ステップ1: MPGArrayを構築する

```
  (a) Aとbを精度TWで保存します。

  (b) 因子分解（Aのコピー）を精度TFで保存します。

  (c) 残差、解のローカルコピー、およびKrylovベクトルのストレージを精度TRで事前に割り当てます。
```

ステップ2: mpglu!を呼び出して因子分解オブジェクトを構築します

`TR`キーワード引数は残差の精度です。何をしているのかわからない限り、これをそのままにしておいてください。デフォルトは`nothing`で、これはソルバーに`TR = TW`を設定するよう指示します。`TR`を設定する場合、それはTWよりも高い精度でなければならず、実質的に`TR.(A) x = TR.(b)`をTFの因子分解でIRを使って解いていることになります。

ここでの興味のあるケースは`TW = Float32; TF = Float16; TR = Float64`です。これらの精度でのIR-GMRESは、時々半精度の救世主となります。

デフォルトの基底サイズは10です。結果に満足していない場合は、これを変更して（すべき）遊んでみてください。十分なベクトルを保存するのに問題がある場合は、IR-BiCGSTAB `mpblu`を試す価値があります。

この例を見てください。

異なるハードウェア、BLAS、Juliaのバージョン、またはこのパッケージでこの例に対して正確に同じ結果が得られない場合があります。私はまだ終了基準を調整しており、反復回数はそれに応じて増減する可能性があります。

## 例

```jldoctest
julia> using MultiPrecisionArrays

julia> using MultiPrecisionArrays.Examples

julia> N=4096; alpha=799.0; AD = I - alpha*Gmat(N); A = Float32.(AD);

# TF=Float16でバニラIRを試す

julia> xe=ones(Float32,N); b=A*xe; AF=mplu(A); 

julia> mout=\(AF, b; reporting=true);

julia> mout.rhist
5-element Vector{Float64}:
 9.88750e+01
 3.92435e+00
 3.34373e-01
 2.02045e-01
 2.24720e-01

# 収束しているようには見えません。TR=Float64はどうですか？

julia> BF=mplu(A; TR=Float64);

julia> mout2=\(BF, b; reporting=true);

julia> mout2.rhist
5-element Vector{Float64}:
 9.88750e+01
 3.92614e+00
 3.34301e-01
 2.01975e-01
 2.24576e-01

# Float16は保存できますか？IR-GMRESはどうですか？

julia> GF=mpglu(A; TR=Float64);

julia> mout3=\(GF, b; reporting=true);

julia> mout3.rhist
6-element Vector{Float64}:
 9.88750e+01
 2.23211e-04
 9.61252e-09
 1.26477e-12
 8.10019e-13
 8.66862e-13

# シャザム！昇格された問題の解を得ましたか？

julia> xp=Float64.(A)\b; norm(xp-mout3.sol,Inf)
9.43157e-12

# はい。
```
