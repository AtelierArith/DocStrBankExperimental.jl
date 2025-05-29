```julia
newton(probPO, orbitguess, defOp, options; kwargs...)

```

この関数は `newton(probPO, orbitguess, options, jacobianPO; kwargs...)` に似ていますが、`defOp` に保存されているものとは異なる周期軌道を見つけるために脱落を使用します。引数の完全な説明については、前述の方法を参照してください。現在の方法は、ニュートン-クリロフアルゴリズムが平衡点に収束するのを防ぐために、ホップ分岐の近傍で使用できます。
