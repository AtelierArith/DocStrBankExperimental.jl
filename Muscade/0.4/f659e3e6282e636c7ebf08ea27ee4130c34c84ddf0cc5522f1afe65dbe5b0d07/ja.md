```
c = coord(node)
```

要素コンストラクタによって使用され、コンストラクタに渡されたノードのベクトルの座標を取得します。`c`は次のようにアクセスされます。

```
c[inod][icoord]
```

ここで、`inod`は要素-ノード番号、`icoord`は座標ベクトルへのインデックスです。

`c[inod]`は`nod[inod].coord`と同じメモリを指していることに注意してください：`c[inod]`を変更しないでください！

参照：[`addnode!`](@ref)、[`addelement!`](@ref)、[`describe`](@ref)、[`solve`](@ref)  
