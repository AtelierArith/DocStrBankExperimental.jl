```
send(service, sender::Actor, to::Addr, messagebody::Any; energy::Real = 1, timeout::Real = 2.0)
```

アクターから別のアクターにメッセージを送信します。

アクターAPIの一部であり、取得した`service`を提供するライフサイクルコールバックから呼び出すことができます。

`messagebody`は任意の型で構いませんが、ノード間通信の現在の制限は、`messagebody`のシリアライズ形式が約100バイトの余裕を持ってIPv4 UDPパケットに収まる必要があることです。正確な値はネットワークのMTUサイズや実装の詳細によって異なりますが、1380バイトは安全と見なすことができます。システムを調整してより高い値を得ることができるかもしれません。

`messagebody`が`Request`の場合、そのトークンのタイムアウトが設定されます。`timeout`キーワード引数を使用して期限（秒）を制御できます。

`energy`は、メッセージに添付されたインフォトンのエネルギーと符号を設定します（インフォトンオプティマイザーが実行中の場合）。

# 例

```julia
const QUERY = "人生、宇宙、すべての究極の質問。"

mutable struct MyActor <: Actor{TCoreState}
    searcher::Addr
    core::CoreState
    MyActor() = new()
end

struct Start end

struct Search
    query::String
end

[...] # 検索者を生成するか、そのアドレスを受け取る


function CircoCore.onmessage(me::MyActor, message::Start, service)
    send(service,
            me,
            me.searcher,
            Search(QUERY, addr(me)))
end
```

# 実装

`service`は、`onmessage`のようなライフサイクルコールバックの最後の引数であることに注意してください。これは、`onmessage`が動的にディスパッチされ、`service`がどこにディスパッチするかに関する情報を提供しないためです。（`v"0.2.0"`の時点で、サービスインスタンスは1つだけ存在します）最後にリストすることでパフォーマンスが向上します。

一方、`send`のようなアクターAPIエンドポイントは常に静的にディスパッチされるため、サービスを最初の引数として受け入れることができ、ユーザーは例えば"`spawn(service`"を思考の単位として扱い、バラスト`service`を書くのを忘れないようにできます。

一貫性は便利さと同じくらい重要です。しかし、パフォーマンスが最優先です。
