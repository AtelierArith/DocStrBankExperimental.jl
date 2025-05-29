```
header(img::AstroImage)
```

AstroImage にラップされた基礎となる FITSIO.FITSHeader オブジェクトを返します。このオブジェクトは、getindex および setindex メソッドがあまり柔軟ではないことに注意してください。シンボル、Comment、History などによるインデックス指定はサポートされていません。
