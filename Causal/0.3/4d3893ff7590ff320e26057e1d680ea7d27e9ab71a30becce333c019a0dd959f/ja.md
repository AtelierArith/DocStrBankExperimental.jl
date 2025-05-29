```julia
readinput!(comp)

```

`comp`の`input`が`Inport`である場合、`comp`の入力値を返します。それ以外の場合は`nothing`を返します。

!!! note
    `comp`の入力値を読み取るには、`comp`を起動する必要があります。参照: [`launch(comp::AbstractComponent)`](@ref)

