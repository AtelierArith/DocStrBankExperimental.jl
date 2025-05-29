```julia
struct IterSVD
```

KrylovKitのGKLアルゴリズムに基づく反復SVDソルバーで、（対称）テンソルに適応されています。ターゲットとする特異値の数は、`ProjectorAlg`の`TruncationSpace`を介して設定されます。特に、これによりターゲットとする特異値をブロック単位で指定することが可能になります。対称ブロックが特異値の数に比べて小さすぎる場合や、反復SVDが収束しなかった場合、アルゴリズムは密なSVDにフォールバックします。

## フィールド

  * `alg::KrylovKit.GKL`
  * `fallback_threshold::Float64`
  * `start_vector::Any`

## コンストラクタ

```
IterSVD(; kwargs...)
```

以下のキーワード引数に基づいて`IterSVD`アルゴリズム構造体を構築します：

  * `alg::KrylovKit.GKL=KrylovKit.GKL(; tol=1e-14, krylovdim=25)` : ブロック単位の反復SVD用のGKLアルゴリズム構造体。
  * `fallback_threshold::Float64=Inf` : `howmany / minimum(size(block))`の閾値で、（ブロックが小さすぎる場合）アルゴリズムがTensorKitの密なSVDにフォールバックするしきい値。
  * `start_vector=random_start_vector` : 反復SVDアルゴリズムの初期ベクトルを提供する関数。
