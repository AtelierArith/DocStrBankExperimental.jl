メッシュ名をワイルドカード形式で検出するように追加します

例えば: simAddDetectionFilterMeshName("Car**") は "Car**" という名前のすべてのインスタンスを検出します

引数:     camera*name (str) カメラの名前。後方互換性のため、0,1などのID番号も使用できます     image*type (ImageType) 必要な画像のタイプ     mesh*name (str) ワイルドカード形式のメッシュ名     vehicle*name (str, optional) カメラに関連付けられた車両     external (bool, optional) カメラが外部カメラであるかどうか
