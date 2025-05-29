```
loadPlan(filename::Union{AbstractString, IO}, modules::Vector{Module})
```

TOMLファイルから`RecoPlan`をロードします。`modules`引数は、プランで使用される型を含むモジュールのベクターです。プランをロードした後、リスナーは`loadListener!`を使用してプロパティに接続されます。
