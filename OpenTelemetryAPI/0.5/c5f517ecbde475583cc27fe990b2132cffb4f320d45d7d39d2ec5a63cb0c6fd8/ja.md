```
Resource(;attributes=nothing, schema_url="", default_attributes=OTEL_RESOURCE_ATTRIBUTES())
```

[仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/overview.md#resources)からの引用：

> Resourceは、テレメトリが記録されるエンティティに関する情報をキャプチャします。たとえば、Kubernetesコンテナによって公開されるメトリクスは、クラスター、名前空間、ポッド、およびコンテナ名を指定するリソースにリンクできます。
>
> Resourceは、エンティティ識別の全階層をキャプチャすることがあります。クラウド内のホストや、プロセス内で実行されている特定のコンテナまたはアプリケーションを説明することができます。

