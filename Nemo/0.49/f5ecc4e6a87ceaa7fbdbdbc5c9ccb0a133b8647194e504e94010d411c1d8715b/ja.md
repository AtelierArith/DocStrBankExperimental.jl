```
guess(R::QQBarField, x::AcbFieldElem, maxdeg::Int, maxbits::Int=0)
guess(R::QQBarField, x::ArbFieldElem, maxdeg::Int, maxbits::Int=0)
guess(R::QQBarField, x::ComplexFieldElem, maxdeg::Int, maxbits::Int=0)
guess(R::QQBarField, x::RealFieldElem, maxdeg::Int, maxbits::Int=0)
```

与えられた数値の囲い `x` から代数数を再構成しようとします。このアルゴリズムは、次数 `maxdeg` までの候補を探し、係数はサイズ `maxbits` まで（指定がない場合は `x` の精度にデフォルト）を探します。適切な代数数が見つからない場合は例外をスローします。

推測には通常、高い精度が必要であり、入力精度が $O(maxdeg \cdot maxbits)$ より小さい場合にこの関数を呼び出すことはあまり意味がありません。この関数が成功した場合、出力は囲い `x` に含まれることが保証されますが、失敗したからといって指定されたパラメータを持つ代数数が存在しないことを証明するものではありません。

この関数は、ターゲットパラメータで単一の反復を行います。最良のパフォーマンスを得るためには、意図した解のサイズが不明であるか、最悪の場合の境界よりもはるかに小さい可能性がある場合に、次第に大きなパラメータでこの関数を繰り返し呼び出すべきです。
