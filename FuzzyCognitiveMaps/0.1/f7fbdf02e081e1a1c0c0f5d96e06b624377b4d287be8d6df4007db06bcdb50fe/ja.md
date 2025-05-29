```
update!(fcm::FuzzyCognitiveMap)
```

`fcm`の単一状態更新ステップを実行します。

非外部概念の状態を次の式を使用して更新します: `new_state = activation(state * weights)`

track_historyが有効な場合、新しい状態は履歴に追加されます。

# 引数

  * `fcm::FuzzyCognitiveMap`: 更新するFCM
