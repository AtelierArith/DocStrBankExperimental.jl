```
voxelquality(phase::AbstractArray; keyargs...)
```

各ボクセルの品質を計算します。ボクセルの品質はマスクを作成するために使用できます。品質の範囲は [0;1] です。

# 例

```julia-repl
julia> qmap = voxelquality(phase_3echo; TEs=[1,2,3]);
julia> mask = robustmask(qmap);
```

`romeo`/`unwrap` と同じ入力を取ります：

関連情報は [`unwrap`](@ref) を参照してください。
