```
SamplerUniformMissRow(constraint::MissRow, H::Int64)
```

`MissRow`制約から`BitVector`オブジェクトを均等にサンプリングするためのデータを事前に計算します。サンプリングされたベクトルの長さは`H`になります。

使用されるアルゴリズムは、Bernardi、Olivier、およびOmer Giménezによる「正規言語からのランダムサンプリングのための線形アルゴリズム」です。Algorithmica 62.1 (2012): 130-145。

# 例

```julia-repl
julia> sp = SamplerUniformMissRow(MissRow(3), 10);

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
