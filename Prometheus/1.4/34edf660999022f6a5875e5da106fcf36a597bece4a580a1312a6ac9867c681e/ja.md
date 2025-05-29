```
Prometheus.remove(family::Family, label_values)
```

`label_values`に対応するコレクタを削除します。実質的にこれによりコレクタがリセットされます。なぜなら、[`Prometheus.labels`](@ref)は同じラベル名で呼び出されるとコレクタを再作成するからです。

`label_values`を指定する方法については、[`Prometheus.labels`](@ref)を参照してください。

!!! note
    このメソッドはラベル名のキャッシュされたコレクタを無効にします。

