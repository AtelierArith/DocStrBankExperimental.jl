```
 word2vec(train, output; size=100, window=5, sample=1e-3, hs=0,  negative=5, threads=12, iter=5, min_count=5, alpha=0.025, debug=2, binary=1, cbow=1, save_vocal=Nothing(), read_vocab=Nothing(), verbose=false,)

トレーニングのためのパラメータ:
    train <file>
        <file> からテキストデータを使用してモデルをトレーニングします
    output <file>
        結果の単語ベクトル / 単語クラスタを保存するために <file> を使用します
    size <Int>
        単語ベクトルのサイズを設定します; デフォルトは 100
    window <Int>
        単語間の最大スキップ長を設定します; デフォルトは 5
    sample <AbstractFloat>
        単語の出現のしきい値を設定します。トレーニングデータで
        より高い頻度で出現する単語はランダムに
        ダウンサンプリングされます; デフォルトは 1e-5。
    hs <Int>
        階層的ソフトマックスを使用します; デフォルトは 1 (0 = 使用しない)
    negative <Int>
        負の例の数; デフォルトは 0、一般的な値は 
        5 - 10 (0 = 使用しない)
    threads <Int>
        <Int> スレッドを使用します (デフォルト 12)
    iter <Int>
        より多くのトレーニングイテレーションを実行します (デフォルト 5)
    min_count <Int>
        <Int> 回未満で出現する単語は破棄されます; デフォルト
        は 5
    alpha <AbstractFloat>
        開始学習率を設定します; デフォルトは 0.025
    debug <Int>
        デバッグモードを設定します (デフォルト = 2 = トレーニング中の詳細情報)
    binary <Int>
        結果のベクトルをバイナリモードで保存します; デフォルトは 0 (オフ)
    cbow <Int>
        単語の連続バックモデルを使用します; デフォルトは 1 (スキップグラム
        モデル)
    save_vocab <file>
        語彙は <file> に保存されます
    read_vocab <file>
        語彙は <file> から読み込まれ、トレーニングデータから構築されません
    verbose <Bool>
        トレーニングの出力を印刷します
```
