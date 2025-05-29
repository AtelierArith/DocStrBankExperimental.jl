```
@witharray(v_arr=v, [size=(dims...)], [mtype=MEM_HOST], body)
```

[`CeedVector`](@ref) `v`の内容を名前`v_arr`の配列として抽出し、`body`を実行します。[`memory type`](@ref MemType) `mtype`が指定されていない場合は、`MEM_HOST`が使用されます。サイズが指定されていない場合は、フラットベクターが想定されます。

# 例

`CeedVector` `v`の内容を反転させる：

```
@witharray v_arr=v v_arr .*= -1.0
```
