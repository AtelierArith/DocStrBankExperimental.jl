```
function emulate
```

ノイズのあるシステムの進化を、ntrajのノイズのある軌道のアンサンブルを平均化することでエミュレートします。出力は、各配列が単一の軌道に対応する時系列に対してoutput_funcの出力を含む配列です。

# 引数

  * `prob`: エミュレートするNoisySchrodingerProblem
  * `ntraj`: シミュレーションに使用する軌道の数
  * `output_func`: Vector{Complex}->Any - 保存する状態ベクトル配列の変換
  * `ensemble_algo`: EnsembleProblemのドキュメントを参照してください。一般的な選択肢はEnsembleSerialとEnsembleThreadedです。
