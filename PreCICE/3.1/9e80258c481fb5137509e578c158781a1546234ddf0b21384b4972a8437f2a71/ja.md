```
createParticipant(participantName::String, configFilename::String, solverProcessIndex::Integer, solverProcessSize::Integer)
```

カップリングインターフェースを作成し、設定します。このインターフェースの他のメソッドが呼び出される前に呼び出す必要があります。

# 引数

  * `participantName::String`: インターフェースを使用しているxml設定からの参加者の名前。
  * `configFilename::String`: xml設定ファイルの名前（パス付き）。
  * `solverProcessIndex::Integer`: ソルバーコードが複数のプロセスで実行される場合、各プロセスはpreCICEを使用するためにそのインデックスを指定する必要があり、インデックスは0から始まり、solverProcessSize - 1で終わる必要があります。
  * `solverProcessSize::Integer`: この参加者がpreCICEを使用しているソルバープロセスの数。

# 例

```julia
createParticipant("SolverOne", "./precice-config.xml", 0, 1)
```
