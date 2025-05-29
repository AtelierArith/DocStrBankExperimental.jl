```
timesum(snoop::Vector{Tuple{Float64, Core.MethodInstance}}, unit = :s)
```

スヌープマクロによって測定された合計時間を計算します。`unit` は :s または :ms です。

# 例

```julia
using SnoopCompile
data = @snoopi begin
    using MatLang
    MatLang_rootpath = dirname(dirname(pathof("MatLang")))

    include("$MatLang_rootpath/test/runtests.jl")
end
println(timesum(data, :ms))
```
