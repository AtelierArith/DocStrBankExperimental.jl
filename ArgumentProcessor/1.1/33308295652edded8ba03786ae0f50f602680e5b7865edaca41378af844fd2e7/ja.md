```julia
Parameter(position::Int; innername::AbstractString="", default::AbstractString="", fmt::AbstractString="%s",
          required::Bool=false, help::AbstractString="")
```

fmt: Cのような入力フォーマットの形式です。この形式は`Varformat`と`Delimiter`の組み合わせであり、outernameの後に追加されます。詳細については[`Varformat`](@Varformat)および[`Delimiter`](@Delimiter)を参照してください。

# 例

1. コマンドライン引数を解析するには:

```shell
   program 0.1
```

引数は次のように設定されます:

```julia
Option(1; fmt="%f")
```

2. コマンドライン引数:

```shell
   program 2022/01/01T00:00:00.0
```

設定:

```julia
Option(1; fmt="%d/%d/%dT%d:%d:%f")
```
