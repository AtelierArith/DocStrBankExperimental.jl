```
SpanContext(;span_id, trace_id, is_remote, trace_flag=TraceFlag(), trace_state=TraceState())
```

`SpanContext`は、分散コンテキストに沿ってシリアライズされ、伝播される必要がある`Span`の部分を表します。`SpanContext`は不変です。

OpenTelemetryの`SpanContext`表現は、[W3C TraceContext仕様](https://www.w3.org/TR/trace-context/)に準拠しています。これは、`TraceId`と`SpanId`という2つの識別子と、一般的な`TraceFlags`およびシステム固有の`TraceState`値のセットを含みます。

`TraceId` 有効なトレース識別子は、少なくとも1つの非ゼロバイトを持つ16バイトの配列です。

`SpanId` 有効なスパン識別子は、少なくとも1つの非ゼロバイトを持つ8バイトの配列です。

`TraceFlags`はトレースに関する詳細を含みます。TraceState値とは異なり、TraceFlagsはすべてのトレースに存在します。仕様の現在のバージョンは、[sampled](https://www.w3.org/TR/trace-context/#sampled-flag)と呼ばれる単一のフラグのみをサポートしています。

`TraceState`は、ベンダー固有のトレース識別データをキーと値のペアのリストとして表現します。TraceStateは、複数のトレースシステムが同じトレースに参加することを可能にします。これは、[W3C Trace Context仕様](https://www.w3.org/TR/trace-context/#tracestate-header)で完全に説明されています。
