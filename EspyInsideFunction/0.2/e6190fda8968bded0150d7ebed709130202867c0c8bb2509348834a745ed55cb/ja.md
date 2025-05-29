```
@espy function residual(x,y)
    ngp=2
    r = 0
    for igp=1:ngp
        :z = x[igp]+y[igp]
        :s,dum  = :material(z)
        r += s
    end
    return r
end
@espy function material(z)
    :a = z+1
    :b = a*z
    return b,3.
end
```

コードの変換後:

```
function residual(x,y)
    ngp=2
    r = 0
    for igp=1:ngp
        z = x[igp]+y[igp]
        s,dum  = material(z)
        r += s
    end
    return r
end
function material(z)
    a = z+1
    b = a*z
    return b,3.
end
```

追加の `out` と `key` 引数を持つコード:

```
function residual(out,key,x,y)
    ngp = 2
    r   = 0
    for igp = 1:ngp
        @espy_loop key gp                     # key_gp = key.gp[igp]
        z = x[igp]+y[igp]
        @espy_record out key_gp z             # out[key_gp.z] = z
        s = @espy_call out key_gp material(z) # s = material(out,key_gp.material,z)
        @espy_record out key_gp s             # out[key_gp.s] = s
        r += s
    end
    return r
end
function material(out,key,z)
    a = z+1
    @espy_record out key a                    # out[key.a] = a
    b = a*z
    @espy_record out key b                    # out[key.b] = b
    return b
end
```

マクロの評価結果:

```
@espy_record out key a
```

は次のように評価されます:

```
if haskey(key,a)
    out[key.a] = a
end
```

`key` は [`@request`](@ref) に基づいて [`makekey`](@ref) によって生成されたデータ構造です。

`out` パラメータを持つ `residual` のバージョンが呼び出されたとき、この出力の内容は `key` を使用してアクセスされます:

```
requestable  = (gp=forloop(2, (z=scalar,s=scalar, material=(a=scalar,b=scalar))),)
requested    = @request gp[].(s,z,material.(a,b))
key,nkey     = makekey(requested,requestable)
residual(out,key,x,y)
igp          = 2
z            = out[key.gp[igp].z]
```

参照: [`@espydbg`](@ref), [`@request`](@ref), [`makekey`](@ref) ```
