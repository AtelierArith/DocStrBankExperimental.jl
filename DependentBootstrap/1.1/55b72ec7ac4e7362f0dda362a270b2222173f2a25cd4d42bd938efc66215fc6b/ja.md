```
dbootlevel1(data::T1, bi::BootInput)
dbootlevel1(data::T1; kwargs...)
```

データセットに関連するレベル1のブートストラップ統計を取得し、BootInputのブートストラップ手法を使用します。

BootInputのキーワードコンストラクタを呼び出すキーワードメソッドも提供されています。使用可能なキーワードの詳細については、REPLで?BootInputを使用してください。

戻り値の型はbi.flevel1によって決定され、これはT1、すなわちtypeof(data)を入力として受け入れる関数でなければなりません。出力型T2は、bi.flevel2がVector{T2}を入力として受け入れる限り、任意の型を返すことができます。

例えば、dataがVector{<:Number}の場合、bi.flevel1は関数meanである可能性があり、この場合はFloat64を返すため、bi.flevel2はVector{Float64}を入力として受け入れることができる関数でなければなりません。

より複雑な例：dataがMatrix{<:Number}の場合、bi.flevel1は匿名関数x->mean(x,dims=1)である可能性があり、この場合は単一行のMatrix{Float64}を返すため、bi.flevel2はVector{Matrix{Float64}}を入力として受け入れることができる関数でなければなりません。
