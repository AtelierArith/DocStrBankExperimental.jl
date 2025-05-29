```
@get_attribute scene (a, b, c, d)
```

これは、`scene`から属性`a`、`b`、`c`、`d`を抽出し、正しい属性変換を適用し、信号であれば値を抽出します。それらの属性を変数として利用可能にし、タプルとして返します。したがって、上記は次のようになります:

```julia
begin
    a = get_attribute(scene, :a)
    b = get_attribute(scene, :b)
    c = get_attribute(scene, :c)
    (a, b, c)
end
```
