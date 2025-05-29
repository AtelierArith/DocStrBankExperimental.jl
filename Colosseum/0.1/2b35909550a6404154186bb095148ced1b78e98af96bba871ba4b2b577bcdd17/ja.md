Runtime Swap Texture API

詳細については https://microsoft.github.io/AirSim/retexturing/ を参照してください

Args:     tags (str) "," || ", " で区切られたタグの文字列で、スワップを実行するアクターを特定します     tex_id (int, optional) スワップを実行する各アクターに割り当てられたテクスチャの配列のインデックス

```
                        もしオブジェクトのテクスチャセットの範囲外であれば、利用可能なテクスチャの数でモジュロを取ります
component_id (int, optional)
material_id (int, optional)
```

Returns:     list[str]: 提供されたタグに一致し、テクスチャスワップが実行されたオブジェクトのリスト
