```
write_xsf(filename::String, wfc::WannierFunction, str::Structure; value_func=x->norm(x))
```

[`WannierFunction`](@ref) と [`Structure`](https://louisponet.github.io/DFControl.jl/stable/guide/structure/) を XCrysden または VESTA で読み取れる xsf ファイルに書き込みます。書き込まれる値は `value_func` によって制御され、これは `wfc.values` の各エントリに使用され、単一の `Number` を出力する必要があります。
