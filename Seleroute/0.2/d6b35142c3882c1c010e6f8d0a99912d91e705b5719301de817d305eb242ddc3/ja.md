ルーティング問題を解決するために使用される定式化のタイプ。このパッケージは、2つの主要な定式化ファミリーをネイティブにサポートしています：

  * `FlowFormulation`: 各エッジがモデルに明示的に存在します
  * `PathFormulation`: モデルはパス変数を使用します。パスベースの定式化は2つの方法で解決できます：

      * パスの事前計算: 事前計算されたパスのセットのみが考慮されます; 事前計算されたパスが不十分な場合、解は近似的であり、近似係数は保証されません
      * 列生成: 解を改善する可能性があるときに、新しいパスがその場で追加されます
