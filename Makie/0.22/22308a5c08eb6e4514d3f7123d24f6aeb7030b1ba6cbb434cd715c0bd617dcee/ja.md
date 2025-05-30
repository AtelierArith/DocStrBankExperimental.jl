```
ispressed(parent, result::Bool[, waspressed = nothing])
ispressed(parent, button::Union{Mouse.Button, Keyboard.Button[, waspressed = nothing])
ispressed(parent, collection::Union{Set, Vector, Tuple}[, waspressed = nothing])
ispressed(parent, op::BooleanOperator[, waspressed = nothing])
```

この関数は、ボタンまたはボタンの組み合わせが押されているかどうかをチェックします。

真または偽が与えられた場合、`ispressed`はそれぞれ真または偽を返します。これにより、外部からインタラクションを「常にオン」または「常にオフ」にする方法が提供されます。

`Keyboard.enter`や`Mouse.left`のようなボタンまたはボタンのコレクションを渡すと、与えられたすべてのボタンが押されている場合に真を返します。

親は、`get_scene`メソッドが実装されている任意のオブジェクトであり、例えばFigure、Axis、Axis3、Lscene、FigureAxisPlot、AxisPlotなどが含まれます。

より複雑なボタンの組み合わせについては、`&`、`|`、および`!`を使用してブール式に組み合わせることができます。例えば、`ispressed(parent, !Keyboard.left_control & Keyboard.c)`や`ispressed(parent, Keyboard.left_control & Keyboard.c)`を使用して、両方のケースが同時にトリガーされるのを避けることができます。

さらに、任意のボタン、ボタンコレクション、またはブール式を排他的にするために、`Exclusively(...)`でラップすることもできます。これにより、`ispressed`は現在押されているボタンが要求と正確に一致する場合にのみ真を返します。

リリースイベントに反応したい場合は、オプションでキーまたはマウスボタン`waspressed`を追加することができ、これは現在の状態に関係なく押されていると見なされます。例えば、マウスボタンイベントに反応する際に、`event.button`を渡すことで、そのボタンを含むキーの組み合わせが依然として真として評価されます。

参照: [`And`](@ref), [`Or`](@ref), [`Not`](@ref), [`Exclusively`](@ref), `&`, `|`, `!`
