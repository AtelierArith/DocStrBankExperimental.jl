```
read_POLAR(filename::String)
```

POLAR形式で保存されたニューラルネットワークを読み込みます。

### 入力

  * `filename` – POLARファイルの名前

### 出力

[`FeedforwardNetwork`](@ref)。

### 注意事項

POLAR形式はSherlockと同じパラメータ形式を使用しています（[`read_Sherlock`](@ref)を参照）が、一般的な活性化関数を許可します。

さらに、最後の2行は次のとおりです：

```
0.0
1.0
```

参照パーサーとライターは[こちら](https://github.com/ChaoHuang2018/POLAR_Tool/blob/8df333a59321f45227dafc87c367779783b6166c/POLAR/neuralnetwork.py)で見つけることができます。
