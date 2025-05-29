```
saveToFITS(map::HealpixMap{T, O}, filename::AbstractString, typechar="D", unit="", extname="MAP") where {T <: Number, O <: Order}
saveToFITS(map::PolarizedHealpixMap{T, O}, filename::AbstractString, typechar="D", unit="", extname="MAP") where {T <: Number, O <: Order}
```

マップをFITSファイルに保存します。ファイルの名前は`filename`で指定されます。`!`で始まる場合、既存のファイルは警告なしに上書きされます。パラメータ`typechar`はFITSファイルで使用されるデータ型を指定します。デフォルト（`D`）は64ビット浮動小数点値を保存します。他の値についてはCCFITSIOのドキュメントを参照してください。キーワード`unit`はマップ内のピクセルに使用される測定単位を指定します。キーワード`extname`はマップピクセルが書き込まれるHDUの名前を指定します。
