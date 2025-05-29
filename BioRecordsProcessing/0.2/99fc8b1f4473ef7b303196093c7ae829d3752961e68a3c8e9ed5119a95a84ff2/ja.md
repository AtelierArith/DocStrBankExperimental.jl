```julia
Directory(directory::String, glob_pattern::String; second_in_pair = nothing)
```

`directory`内の`glob_pattern`に一致するすべてのファイルをリストします（[Glob.jl](https://github.com/vtjnash/Glob.jl)を参照）。ペアファイルの場合、ペアの最初のファイルのファイル名を引数として受け取り、2番目のファイルのファイル名を返す関数を提供できます。

```@example
Directory(input_directory, "*.fastq")
```
