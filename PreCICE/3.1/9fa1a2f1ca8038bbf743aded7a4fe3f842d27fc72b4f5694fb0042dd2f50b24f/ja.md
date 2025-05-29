```
requiresMeshConnectivityFor(meshName::String)::Bool
```

与えられたメッシュが接続情報を必要とするかどうかをチェックします。

preCICEは、ソルバーから接続情報を必要とする場合があり、必要でない場合は接続に関するAPI呼び出しを無視します。この関数を使用して、条件に応じてこの接続を生成します。
