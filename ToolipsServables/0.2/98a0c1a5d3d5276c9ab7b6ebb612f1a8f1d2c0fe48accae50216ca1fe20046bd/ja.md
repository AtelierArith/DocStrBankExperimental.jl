```julia
interpolate!(mdcomp::Component{:div}, components::Component{<:Any} ...; keyargs ...) -> ::Nothing
interpolate!(comp::Component{:div}, fillfuncs::Pair{String, <:Any} ...) -> ::Nothing
```

`div`の`:text`内にマークダウンを補間します（通常は`tmd`を使用して作成されます）。`Component{<:Any}`およびキーワード引数のディスパッチは、インラインコードブロックや、その前に`%`が付いた値を補間します。後者の関数は、関数とペアになった一連の文字列を受け取ります。

関数はコードブロックの`String`を受け取り、戻り値は別の`String` – 結果です。
