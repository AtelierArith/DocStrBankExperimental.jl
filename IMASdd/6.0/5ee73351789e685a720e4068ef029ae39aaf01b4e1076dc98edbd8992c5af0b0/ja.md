```
cocos_transform(@nospecialize(ids::IDS), field::Symbol)
```

指定されたIDSの位置に対してcocos_transformの文字列ベクターを返します

  * 手動で割り当てられていないCOCOS変換の場合は空のベクター
  * 一要素のベクターは以下で満たされます

      * COCOS変換がない場合は`""`
      * 手動で割り当てられるべきだったがされていないCOCOS変換の場合は`"?"`
      * `CoordinateConventions.jl`パッケージに従ってcocos変換を定義する他の文字列
