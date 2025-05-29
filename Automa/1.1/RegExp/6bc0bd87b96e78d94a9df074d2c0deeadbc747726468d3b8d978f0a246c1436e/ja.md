```
precond!(re::RE, s::Symbol; [when=:enter], [bool=true]) -> re
```

`re`の前提条件を`s`に設定します。`re`への状態遷移の前、または`re`の内部では、遷移が行われる前に前提条件コード`s`が`bool`であることがチェックされます。

`when`は、条件が正規表現に入るとき（`:enter`の場合）にチェックされるか、正規表現の内部でのすべての状態遷移のたびにチェックされるか（`:all`の場合）を制御します。

# 例

```julia
julia> regex = re"ab?c*";

julia> regex2 = precond!(regex, :some_condition);

julia> regex === regex2
true
```
