```
key = makekey(requested,requestable)
```

「key」を作成します。これは、`@espy`によって生成されたコードから返される内部結果の配列`out`へのインデックスのデータ構造です。

入力は次のとおりです。

  * `requested` はリクエストを定義するデータ構造です。この入力は、どの結果を抽出するかを指定するためにコードのユーザーによって提供されます。
  * `requestable` は、特定の関数からリクエストできる中間結果の名前とサイズを定義する名前付きタプルです。この入力は提供されます。

# 例

```
requestable  = (gp=forloop(2, (z=scalar,s=scalar, material=(a=scalar,b=scalar))),)
requested    = @request gp[].(s,z,material.(a,b))
key,nkey     = makekey(requested,requestable)
```

次のような`key`を返します。

```
key.gp[1] == (s=1, z=2, material = (a=3, b=4))
key.gp[2] == (s=5, z=6, material = (a=7, b=8))
key.gp[2].material.a == 7
nkey      == 8
```

参照: [`@espy`](@ref), [`@espydbg`](@ref), [`@request`](@ref), [`forloop`](@ref), [`scalar`](@ref)
