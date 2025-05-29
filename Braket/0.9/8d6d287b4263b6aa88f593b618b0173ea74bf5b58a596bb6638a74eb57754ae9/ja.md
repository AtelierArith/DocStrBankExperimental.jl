```
IRType
```

`Ref{Symbol}`で、デフォルトで使用するIR出力形式を記録します。現在、2つの形式がサポートされています：

  * `:JAQCD`、Amazon Braket IR
  * `:OpenQASM`、OpenQASM3表現

デフォルトでは、`IRType`は`:OpenQASM`を使用するように初期化されていますが、将来的に変更される可能性があります。現在のデフォルト値は、`IRType[]`を呼び出すことで確認できます。デフォルトのIR形式を変更するには、`IRType[]`を設定します。

# 例

```jldoctest
julia> IRType[]
:OpenQASM

julia> IRType[] = :JAQCD;

julia> IRType[]
:JAQCD

julia> IRType[] = :OpenQASM;
```
