```
  SeisProcess(in,out,operators,parameters;<keyword arguments>)
```

ディスクから読み書きする処理フローを実行します

fは次の構文を持つ関数です: d2,h2 = f(d1,h1,e1,param)、ここでparamは関数のキーワード引数のリストです。fは関数のベクトルである可能性があることに注意してください。それらは同じトレースのグループに対して順次実行されます。

# 引数

  * `in::String`: 入力ファイル名
  * `out::String`: 出力ファイル名
  * `key=[]`
