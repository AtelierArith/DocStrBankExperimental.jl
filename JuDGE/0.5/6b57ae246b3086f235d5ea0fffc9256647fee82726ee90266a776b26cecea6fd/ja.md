```
resolve_subproblems(judge::JuDGEModel)
```

JuDGEモデルが収束した後、各ノード内で最適な決定を見つけるためにサブプロブレムを再解決する必要があります。

### 必要な引数

`jmodel` は、解決したいJuDGEモデルです。

### オプションの引数

`force_match` がtrueの場合、サブプロブレム内のすべての拡張およびシャットダウン変数がマスタープロブレムと正確に一致するように強制します。

### 例

```
resolve_subproblems(judge)
```
