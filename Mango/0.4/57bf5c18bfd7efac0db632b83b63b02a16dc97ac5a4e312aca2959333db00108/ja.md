```
calculate_communication(communication_sim::CommunicationSimulation, clock::Clock, messages::Vector{MessagePackage})::CommunicationSimulationResult
```

特定の通信シミュレーションタイプを使用して通信を計算します。現在のシミュレーション時間 `clock` と、このステップで送信されるメッセージ `messages`。
