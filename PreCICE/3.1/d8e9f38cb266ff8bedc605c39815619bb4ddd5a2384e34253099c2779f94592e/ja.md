```
createParticipantWithCommunicator(participantName::String, configFilename::String, solverProcessIndex::Integer, solverProcessSize::Integer, communicator::Union{Ptr{Cvoid}, Ref{Cvoid}, Ptr{Nothing}})
```

TODO: ドキュメントまたは [WIP] タグ。コミュニケーターのデータ型はまだ検証されていません。

# 参照:

[`createParticipant`](@ref)

# 引数

  * `participantName::String`: インターフェースを使用しているxml構成からの参加者の名前。
  * `configFilename::String`: xml構成ファイルの名前（パス付き）。
  * `solverProcessIndex::Integer`: ソルバーコードが複数のプロセスで実行される場合、各プロセスはそのインデックスを指定する必要があり、0から始まりsolverProcessSize - 1で終わる必要があります。
  * `solverProcessSize::Integer`: preCICEを使用しているこの参加者のソルバープロセスの数。
  * `communicator::Union{Ptr{Cvoid}, Ref{Cvoid}, Ptr{Nothing}}`: TODO ?
