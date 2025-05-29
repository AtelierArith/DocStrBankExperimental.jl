```
write_ASAGI(fname::String, Data::CartData; 
                    fields::Union{Nothing, Tuple}=nothing, 
                    km_to_m::Bool=false)
```

CartData構造体`Data`をASAGIファイルに書き込みます。このファイルはSeisSolまたはExaHypeによって読み取ることができます。書き込むフィールドのタプルをオプションで渡すことができます。個々の（スカラー）フィールドのみをディスクに書き込むことができるため、ベクトルまたはテンソルフィールドは最初に分割する必要があります。
