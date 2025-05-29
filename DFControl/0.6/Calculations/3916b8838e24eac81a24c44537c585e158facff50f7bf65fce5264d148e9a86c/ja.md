```
Calculation{P<:Package}(name    ::String;
                        flags   ::AbstractDict = Dict{Symbol, Any}(),
                        data    ::Vector{InputData} = InputData[],
                        exec    ::Exec,
                        run     ::Bool = true,
                        infile  ::String = P == Wannier90 ? name * ".win" : name * ".in",
                        outfile ::String = name * ".out")
```

パッケージ `P` の *DFT* 計算の表現であり、`infile` に書き込まれる `flags`、実行可能ファイル `exec`、および計算によって `outfile` に書き込まれる出力を保持します。これは本質的に `exec < infile.in > outfile.out` に似たジョブスクリプトの行を表します。 `outdata` は、少なくとも一度読み取られた後の解析された計算出力を格納します。 `run` フィールドは、計算が実際に実行されるべきかどうかを示します。例えば、`run=false` の場合、対応する行はジョブスクリプトでコメントアウトされます。

```
Calculation{P<:Package}(name::AbstractString, flags::Pair{Symbol, Any}...; kwargs...)
```

`name` と `flags` から [`Calculation`](@ref) を作成し、他の `kwargs...` はコンストラクタに渡されます。

```
Calculation(template::Calculation, name::AbstractString, flags::Pair{Symbol, Any}...; excs=deepcopy(template.exec), run=true, data=nothing)
```

`template` から新しい [`Calculation`](@ref) を作成し、新しく作成されたものの `flags` を指定されたものに設定します。
