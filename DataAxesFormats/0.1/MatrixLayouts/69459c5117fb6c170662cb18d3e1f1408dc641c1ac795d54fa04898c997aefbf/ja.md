```
check_efficient_action(
    source_file::AbstractString,
    source_line::Integer,
    operand::AbstractString,
    matrix::AbstractMatrix,
    axis::Integer,
)::Nothing
```

これは、`matrix`に対して実行される`operand`のコードがデータの「グレインに沿って」機能するかどうかを確認します。これには、`matrix`が`axis`-メジャーレイアウトである必要があります。そうでない場合は、[`inefficient_action_handler`](@ref)を適用します。通常、これは直接呼び出されることはありません。代わりに[`@assert_matrix`](@ref)を使用してください。

一般的に、データの「グレインに沿って」操作を行うことが**本当に**望ましいです。残念ながら、Julia（およびPython、R、matlab）は、操作を「グレインに逆らって」静かに実行してしまうため、**非常に**遅くなります。この関数をコードに広く適用することで、そのような遅延を検出するのに役立ち、問題を特定するためにコードのプロファイリングに頼る必要がなくなります。

!!! note
    これは、列メジャー行列に対して`selectdim(matrix, Rows, 1)`のような「グレインに逆らった」操作を防ぐものではありませんが、行列に対して一連の操作を実行する前にこのチェックを追加すれば、そのような操作が発生するかどうかを明確に示すことができます。その後、データに対して[`relayout!`](@ref)を呼び出すか、（`Daf`から取得したデータの場合は）単に他のメモリレイアウトを照会するかを検討できます。

