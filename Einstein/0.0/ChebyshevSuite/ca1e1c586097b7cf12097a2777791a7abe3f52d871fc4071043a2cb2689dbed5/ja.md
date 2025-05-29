```
cheb_filter_matrix(weights::AbstractVector{TF}, S::AbstractMatrix{TF}, A::AbstractMatrix{TF}; negsum::Bool=true) where TF<:AbstractFloat
```

事前に計算された重みと演算子を使用してフィルタ行列を構築します。これは、Chebyshevコレクション法のためのもので、オプションで「負の合計トリック」を適用します。このトリックは、私のテストによるとシミュレーションをより安定させるようです。

# 引数

  * `weights`: フィルタ重みのベクトル
  * `S`: Chebyshev合成行列：Chebyshev系列をChebyshevグリッド点での関数値にマッピングします
  * `A`: Chebyshev分析行列：Chebyshevグリッド点での関数値をChebyshev系列にマッピングします
  * `negative_sum_trick`: 負の合計トリックのためのブールフラグ（デフォルト：true）

この関数は、重みを対角スケーリングを通じて適用し、`negative_sum_trick`がtrueのときに対角要素に対して負の合計トリックを実装します。
