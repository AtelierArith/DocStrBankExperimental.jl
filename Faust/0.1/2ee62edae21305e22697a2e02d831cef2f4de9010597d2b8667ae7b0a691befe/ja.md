```
compute!(d)
```

`d.block_size` サンプルの信号を計算し、`d.outputs` (d.block*size, n*outputs) を返します。

この関数を呼び出す前に、`d.inputs` に次元 (d.block*size, n*inputs) の受信信号行列を割り当てる必要があります。

# 例

```julia-repl
julia> d = init!(compile("import("stdfaust.lib"); process = os.oscs(440);"));
julia> compute!(d)
256×1 Matrix{Float32}:
1.0
0.99607
0.9882256
0.9764974
0.96093166
0.9415895
0.9185469
⋮
-0.99841714
-1.0004897
-0.9986304
-0.99284655
-0.98316085
-0.96961135
-0.9522513
```
