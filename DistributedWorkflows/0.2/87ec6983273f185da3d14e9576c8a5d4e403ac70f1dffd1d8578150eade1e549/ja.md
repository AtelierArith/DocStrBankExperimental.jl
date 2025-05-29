```
compile_workflow(workflow::String, build_dir::String)
```

ワークフローのパスとビルドディレクトリのアクセス可能な場所を指定すると、この関数はXMLワークフローをコンパイルします。

注意:   workflow => xpnetファイルへの絶対パス   build_dir => ビルドディレクトリへのパス

# 例

```julia-repl
tmp_dir = joinpath(@__DIR, "tmp")
julia> compile_workflow(joinpath(tmp_dir, "hello_julia.xpnet"))
...
成功: ワークフローがコンパイルされました

```

他にも [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref), [`generate_workflow`](@ref) を参照してください。
