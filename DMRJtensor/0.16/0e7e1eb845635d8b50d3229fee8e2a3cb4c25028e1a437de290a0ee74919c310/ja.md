```
mpo = makeMPO(H,physSize,Ns[,lower=])
```

関数がバルクMPOテンソル`H`を生成し、入力`i`はサイトインデックスで、MPO`mpo`に変換されます。`physSize`はベクトル（各サイトの物理インデックスサイズの要素が1つ）です。`lower`は入力が下三角形形式であることを示し（デフォルト）、テンソルは図式的に次のように表されます。

```
     s2
     |
```

a1 – W – a2       =    W[a1,s1,s2,a2]          |          s1

# 例:

```julia
spinmag = 0.5;Ns = 10
Sp,Sm,Sz,Sx,Sy,O,Id = spinOps(spinmag)
function H(i::Integer)
    return [Id O O;
            Sz O O;
            O Sz Id]
end
isingmpo = makeMPO(H,size(Id,1),Ns)
```
