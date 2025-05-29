```
 word2phrase(train, output; min_count=5, threshold=100, debug=2)

トレーニングのためのパラメータ:
train <file>
      <file> からテキストデータを使用してモデルをトレーニングします 
output <file>
          結果の単語ベクトル / 単語クラスタ / フレーズを保存するために <file> を使用します
min_count <Int>
          <int> 回未満で出現する単語は破棄されます; 
          デフォルトは 5
threshold <AbstractFloat>
  	      <AbstractFloat> 値はフレーズを形成するための閾値を表します（高いほどフレーズは少なくなります）; デフォルトは 100
debug <Int>
      デバッグモードを設定します（デフォルト = 2 = トレーニング中の詳細情報が多い）
```
