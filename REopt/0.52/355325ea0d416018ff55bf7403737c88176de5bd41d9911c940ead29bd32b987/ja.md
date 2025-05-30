```
easiur_data(; latitude::Real, longitude::Real, inflation::Real)
```

この関数は、EASIURデータセットからNOx、SO2、およびPM2.5のコスト（グリッドおよび現場排出用）とコストエスカレーション率を取得します。

この関数は、REopt APIの/easiur_costsエンドポイントで使用され、特にREoptを実行する前に健康排出コスト/エスカレーションのデフォルトを表示するためのウェブツールに使用されますが、REoptを実行せずにEASIURデータにアクセスするための一般的な外部手段でもあります。
