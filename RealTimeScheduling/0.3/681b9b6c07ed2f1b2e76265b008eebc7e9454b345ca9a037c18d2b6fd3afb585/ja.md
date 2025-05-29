```
SamplerUniformMeetAny(constraint::MeetAny, H::Int64)
```

`MeetAny` 制約から `BitVector` オブジェクトを均等にサンプリングするためのデータを事前に計算します。サンプリングされたベクトルの長さは `H` になります。

使用されるアルゴリズムは、Bernardi、Olivier、およびOmer Giménezによる再帰的RGAであり、「A linear algorithm for the random sampling from regular languages。」Algorithmica 62.1 (2012): 130-145です。

# 例

```julia-repl
julia> sp = SamplerUniformMeetAny(MeetAny(1, 3), 10);

julia> rand(sp)
10-element BitVector:
1
1
0
1
1
0
1
0
0
1
```
