```markdown
mpblu(A::AbstractArray{TW,2}; TF=Float32, TR=nothing, i           residterm=residtermdefault) where TW <: Real

多倍精度BiCGSTAB対応配列のコンストラクタと因子分解を組み合わせます。

ステップ1: MPBArrayを構築します。

ステップ2: mpblu!を呼び出して因子分解オブジェクトを構築します。

ステップ3: BiCGSTABが必要とする内部ベクトルを割り当てます。

IR-Krylov法は半精度の救世主として設計されました。したがって、mpgluと同様に、いくつかの例を通じて実行します。ここでの違いは、保存するKrylov基底がないことです。

以下は`mpglu`からの例です。

異なるハードウェア、BLAS、Juliaのバージョン、またはこのパッケージでこの例の結果が正確に同じになるとは限りません。私はまだ終了基準に取り組んでおり、反復回数はそれに応じて増減する可能性があります。

#例

```

jldoctest julia> using MultiPrecisionArrays

julia> using MultiPrecisionArrays.Examples

julia> N=4096; alpha=799.0; AD = I - alpha*Gmat(N); A = Float32.(AD);

# TF=Float16でバニラIRを試す

julia> xe=ones(Float32,N); b=A*xe; AF=mplu(A);

julia> mout=(AF, b; reporting=true);

julia> mout.rhist 5-element Vector{Float64}:  9.88750e+01  3.92435e+00  3.34373e-01  2.02045e-01  2.24720e-01

# 収束しているようには見えません。TR=Float64はどうですか？

julia> BF=mplu(A; TR=Float64);

julia> mout2=(BF, b; reporting=true);

julia> mout2.rhist 5-element Vector{Float64}:  9.88750e+01  3.92614e+00  3.34301e-01  2.01975e-01  2.24576e-01

# これは`mpglu`のドキュメントでの位置です。IR-BiCGSTABを試してみます。

julia> GF=mpblu(A; TR=Float64);

julia> mout3=(GF, b; reporting=true);

julia> mout3.rhist 4-element Vector{Float64}:  9.88750e+01  2.16858e-11  8.38440e-13  8.81073e-13

# これはIR-GMRESとは非常に異なります。その理由は、Krylov部分空間がないため、Krylov反復に制限がないからです。

# したがって、線形作業は最初の反復で残差を大幅に削減します。

# もちろん、私たちは正しく解決し、昇格された問題を解決しました。

julia> xp=Float64.(A)\b; norm(xp-mout3.sol,Inf) 1.63376e-11

```

```
