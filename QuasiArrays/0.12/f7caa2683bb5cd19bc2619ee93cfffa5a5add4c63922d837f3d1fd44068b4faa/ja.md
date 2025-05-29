Inclusion(domain)

ドメインの包含演算子を AbstractQuasiVector として表します。つまり、`v = Inclusion(domain)` の場合、`v[x] == x` は `x in domain` の場合に成り立ち、それ以外の場合は `DomainError` をスローします。

包含はドメインを軸に変換するのに役立ちます。また、オフセット配列に対する `Slice` と同じ役割を果たします。
