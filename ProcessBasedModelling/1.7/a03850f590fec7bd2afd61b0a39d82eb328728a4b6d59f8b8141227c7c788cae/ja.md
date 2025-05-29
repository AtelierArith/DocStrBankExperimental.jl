```
@convert_to_parameters vars...
```

すべての変数 `vars` を `@parameters` に変換し、名前は `vars` と同じで、デフォルト値は `vars` の値と同じにします。このマクロは、`Num` 型の入力は変更せず、すでにパラメータであると仮定します。また、[`LiteralParameter`](@ref) の入力はそのリテラル値に置き換えます。このマクロは、キーワード引数を名前付きパラメータに変換するのに非常に便利で、ユーザーがカスタムパラメータ名を指定したり、一部のキーワードを数値リテラルのままにしておくことも可能です。

例:

```
julia> A, B = 0.5, 0.5
(0.5, 0.5)

julia> C = first(@parameters X = 0.5)

julia> @convert_to_parameters A B C
3-element Vector{Num}:
 A
 B
 X

julia> typeof(A) # `A` はもう数値ではありません!
Num

julia> default_value(A)
0.5

julia> C # バインディング `C` はまだパラメータ `:X` に対応しています!
 X
```
