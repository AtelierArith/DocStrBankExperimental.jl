```
restrict(ivref::GeneralVariableRef, supps...)::GeneralVariableRef
```

無限変数/導関数 `ivref` の入力ドメインを無限パラメータおよび/または値 `supps` に従って制限します。ここで `supps` は `ivref` の無限パラメータのフォーマットに一致する必要があります。以下の出力が可能です：

  * `supps` が完全なサポートポイントである場合、`@variable(model, variable_type = Point(ivref, supps...)` と同等です。
  * `supps` が部分的なサポートポイントである場合、`@variable(model, variable_type = SemiInfinite(ivref, supps...)` と同等です。

便利なことに、このメソッドは `ivref(supps...)` を呼び出すことでも利用できます。

`ivref` が無限変数または導関数でない場合、または `supps` のフォーマットが不正な場合はエラーになります。`supps` が無限パラメータのみを含む場合は警告を表示し、単に `ivref` を返します。

**例**

```julia-repl
julia> restrict(y, 0, x)
y(0, [x[1], x[2]])

julia> restrict(y, 0, [0, 0])
y(0, [0, 0])

julia> y(0, x)
y(0, [x[1], x[2]])

julia> y(0, [0, 0])
y(0, [0, 0])
```
