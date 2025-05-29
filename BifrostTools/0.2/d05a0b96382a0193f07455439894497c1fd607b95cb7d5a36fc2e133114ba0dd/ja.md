```
get_snap_numbers(
    expdir::String,
    expname::String="none"
    ;
    findall::Bool=false,
    filenames::Vector{String}=String[]
    )
```

実験ディレクトリ `exp*dir` 内の 'expname*XXX.snap' 形式のすべてのファイルを見つけ、スナップショット XXX のベクターを返します。`expname` が指定されていない場合、シミュレーションのディレクトリが実験名と一致するものと見なされます。
