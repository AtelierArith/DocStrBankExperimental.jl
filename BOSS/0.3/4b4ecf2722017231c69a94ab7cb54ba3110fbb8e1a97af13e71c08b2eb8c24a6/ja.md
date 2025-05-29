全体のBOSSアルゴリズムの終了条件を指定します。このタイプを継承してカスタム終了条件を定義します。

例: `struct CustomCond <: TermCond ... end`

すべての終了条件は次のメソッドを実装する必要があります: `(cond::CustomCond)(problem::BossProblem)`

このメソッドは、最適化を継続するためにtrueを返し、最適化を終了する必要がある場合はfalseを返します。

参照: [`IterLimit`](@ref)
