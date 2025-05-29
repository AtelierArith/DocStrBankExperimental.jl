```
mpo = makeMPO(H,physSize,Ns[,lower=])
```

バルクMPOテンソル`H`を`Ns`サイト用に変換します。`physSize`はベクトルで（各サイトの物理インデックスサイズの要素が1つ）、`lower`は入力が下三角形形式であることを示します（デフォルト）で、テンソルは図式的に次のように表されます。

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
