```julia
Option(innername::AbstractString; outername::AbstractString="", abbr::AbstractString="",
       default::AbstractString="", fmt::AbstractString="%s", required::Bool=false, help::AbstractString="")
```

fmt: Cのような入力形式のフォーマット記述。記述は`Varformat`と`Delimiter`の組み合わせであり、outernameの後に追加されます。詳細については[`Varformat`](@Varformat)および[`Delimiter`](@Delimiter)を参照してください。

# 例

コマンドライン引数を解析するには:

```shell
program --test=0.1/0.2
```

引数は次のように設定されます:

```julia
Option("test"; fmt="=%f/%f")
```
