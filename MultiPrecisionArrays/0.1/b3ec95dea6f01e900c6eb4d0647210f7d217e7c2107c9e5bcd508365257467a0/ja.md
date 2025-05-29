mplu(A::AbstractArray{TW,2}; TF=nothing, TR=nothing, residterm=residtermdefault,                     onthefly=nothing) where TW <: Real

多倍精度配列のコンストラクタと因子分解を組み合わせます。

ステップ 1: MPArray を構築します。

```
  (a) A と b を精度 TW で保存します。

  (b) 因子分解（A のコピー）を精度 TF で保存します。

  (c) 残差と解のローカルコピーのために、精度 TR でストレージを事前に割り当てます。
```

ステップ 2: 低精度コピーを因子分解し、因子分解オブジェクトを返します。

`TR` キーワード引数は残差の精度です。自分が何をしているのか分からない限り、これをそのままにしておいてください。デフォルトは `nothing` で、これはソルバーに `TR = TW` を設定するよう指示します。`TR` を設定する場合、それは TW よりも高い精度でなければならず、実質的に `TR.(A) x = TR.(b)` を IR で解いていることになります。MPArray 構造体は解と残差を精度 `TR` で保存し、残差計算は `TR.(A) x` を介して行われます。精度間の転送はオンザフライで行われます。したがって、ストレージコストは行列と因子分解精度のコピーです。

古典的なケースは `TW = TF = Float32` で `TR = Float64` です。これの厄介な部分は、行列のコピーを 2 つ保存しなければならないことです。1 つは残差計算用、もう 1 つは因子で上書きするためのものです。A が非常に条件が悪い場合を除いて、これは良い取引だとは思いません。私のサポートは `mplu` を通じて行われます。これを行うには、`mplu` への呼び出しで `TR` キーワード引数を明示的に指定する必要があります。

キーワード引数 `residterm` は終了基準を設定します。`residterm == true`（デフォルト）は小さな残差で反復を終了します。`residterm == false` は小さなノルム逆誤差で反復を終了します。詳細についてはドキュメントを参照してください。

異なるハードウェア、BLAS、Julia のバージョン、またはこのパッケージで、この例の結果が正確に同じになるとは限りません。私はまだ終了基準を調整しており、その過程で反復回数が増減する可能性があります。

## 例

```jldoctest
julia> using MultiPrecisionArrays.Examples

julia> n=31; alpha=Float32(1.0);

julia> G=Gmat(n, Float32);

julia> A = I + alpha*G;

julia> b = A*ones(Float32,n);

# TF=TW=Float32 および TR=Float64 で mpa を使用

julia> AF = mplu(A; TF=Float32, TR=Float64, onthefly=true);

# 解を求め、反復履歴を保存

julia> mout = \(AF, b; reporting=true);

julia> mout.rhist
5-element Vector{Float64}:
 1.12500e+00
 1.74765e-07
 3.10862e-14
 6.66134e-16
 2.22045e-16

# これは何を意味するのか。昇格された問題を解きます。TR.(A) x = b

julia> AD=Float64.(A);

julia> xd = AD\b;

julia> norm(xd - mout.sol,Inf)
1.11022e-15

# したがって、TR > TW の IR は昇格された問題を解決します。
```
