```
abstract type FlowFields
```

流場（配列としてグリッド化された）へのアクセスを提供するデータ構造であり、後で個々の位置に速度を補間するために使用されます（`Individuals` 構造体に埋め込まれた後）。 

`MITgcm`（https://mitgcm.readthedocs.io）でも使用されているC-gridの規約に従い、流場は次のようにずれていることが期待されます：グリッドセルi,jの中心はi-1/2,j-1/2に位置し、対応する`u[i,j]`（および`v[i,j]`）はi-1,j-1/2（およびi-1/2,j-1）に位置します。 

また、慣例として、速度場はサポートされている`FlowFields`コンストラクタのいずれかに送信する前に、グリッド単位（例：m/sではなく1/s）に正規化されていることが期待されます（`Array`または`MeshArray`を使用）：

```
uvArrays(u0,u1,v0,v1,T)
uvwArrays(u0,u1,v0,v1,w0,w1,T)
uvMeshArrays(u0,u1,v0,v1,T,update_location!)
uvwMeshArrays(u0,u1,v0,v1,w0,w1,T,update_location!)
```

`u0`などの型によって選択される`FlowFields`コンストラクタを使用します。例えば：

```
F=FlowFields(u,u,v,v,0*w,1*w,[0.0,10.0])
F=FlowFields(u,u,v,v,[0.0,10.0],func)
```

オンラインドキュメントの例に示されているように。
