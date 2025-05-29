unscented*transform(b::GaussianBelief, λ::Int=2, α::Number=1,     β::Number=0; decomp*method::String = "cholesky")

単一のGaussianBelief（平均と共分散）を、状態空間の次元数nに基づいて2n+1のシグマ点のセットに変換します。点の配列と、平均および共分散計算に使用される重みの配列を返します。α/βパラメータに基づく別の共分散重み付けのためにProbRobからの定式化を使用しますが、これは必須ではありません。
