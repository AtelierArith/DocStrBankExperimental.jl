```
GroupViaPairwiseComparison <: GroupingConfig
GroupViaPairwiseComparison(; threshold::Real, metric...)
```

[`AttractorsViaFeaturizing`](@ref)で特徴をグループ化する方法に関する指示を含む構造体を初期化します。`GroupViaPairwiseComparison`は、特徴間のペアワイズ距離を考慮して特徴をグループ化し、クラスタを特定します。これは`GroupViaClustering`のクラスタリング手法の代替として使用でき、よりシンプルで、通常は高速で、メモリを少なく使用するという利点があります。

## キーワード引数

  * `threshold = 0.1`: 同じクラスタと見なされるために2つの特徴が持つことができる最大距離を定義する実数 - 閾値を超えると、特徴は異なると見なされます。この値は、クラスタを区別するのに十分大きい必要があります。`threshold`の良い値は、選択したメトリック内のクラスタ内の特徴の変動性や、特徴が再スケーリングされているかどうかに依存します。詳細については、以下の説明を参照してください。
  * `metric = Euclidean()`: 2つの特徴`a`と`b`の距離を返す関数`metric(a, b)`で、`featurizer`の出力です。ここでは、Distances.jlの任意の`Metric`を使用できます。
  * `rescale_features = true`: trueの場合、抽出された特徴の各次元を`[0, 1]`の範囲に別々に再スケーリングします。これは通常、デフォルトの`metric.threshold`に対してより正確なグループ化をもたらしますが、システムに1つのアトラクタしかない場合には避けるべきです。なぜなら、それが同じ位置に多くの異なるアトラクタとして誤って分類されることにつながるからです。

## 説明

このアルゴリズムは、特徴が明確に異なるクラウドに分離されていることを前提とし、クラウドの最大半径は`threshold`によって制御されます。システムが決定論的であるため、これは十分な良さの`featurizer`関数を使用し、過渡状態を除去し、十分に長い間軌道を実行することで達成可能です。その後、`metric`を使用して計算されたペアワイズ距離が`threshold`以下である場合、特徴は同じアトラクタに属すると見なし、距離が大きい場合は異なるアトラクタに属すると見なします。アトラクタは、類似した特徴の各グループに対応します。このようにして、重要なパラメータ`threshold`は、基本的に同じアトラクタに属する特徴に許容される変動の量です。適切に選ばれれば、その値は比較的小さく、微調整する必要はありません。

`threshold`はバランスを取る必要があります。一方では、同じアトラクタからの特徴の変動を考慮するのに十分大きい必要があります - それが十分大きくない場合、アルゴリズムは重複したアトラクタを見つけます。もう一方では、異なるアトラクタからの特徴を一緒にグループ化しないのに十分小さくする必要があります。これは、特徴がどれだけ広がっているかについての知識を必要とします。もしそれが大きすぎると、アルゴリズムはいくつかのアトラクタを見逃し、2つ以上の異なるアトラクタを一緒にグループ化します。したがって、経験則として、比較的大きな値から始めて、重複が現れず、アトラクタが見つからなくなるまで値を減らす手順を数回繰り返すことができます。

このメソッドは、Nが特徴の数であるとき、メモリとパフォーマンスの両方でO(N)としてスケールします。これは、[`GroupViaClustering`](@ref)のO(N^2)と比較して大きな違いです。 ```
