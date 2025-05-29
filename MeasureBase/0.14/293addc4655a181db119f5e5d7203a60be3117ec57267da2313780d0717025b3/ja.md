```
massof(m)
```

測度の*質量*を取得します - つまり、測度をそのサポート上で積分します。

`massof` 

---

```
massof(m, dom)
```

測度 `m` を「ドメイン」 `dom` 上で積分します。ドメインは普遍的に定義されているわけではなく、特定の測度に特有である場合があります。もし `m` が `<:AbstractMeasure` であれば、ユーザーは `m(dom)` と書くこともできます。新しい測度の場合、ユーザーは新しい「呼び出し」メソッドを追加するのではなく、`MeasureBase.massof` を拡張するべきです。

例えば、`rootmeasure(m) == LebesgueBase()` の多くの一変量測度 `m` に対して、ユーザーは `massof(m, a_b)` を呼び出すことができます。ここで `a_b::IntervalSets.Interval` です。

`massof` はしばしば `Real` を返します。しかし、多くの場合、質量が有限であることしかわからないか、全く何もわからない場合があります。これらのケースでは、それぞれ `UnknownFiniteMass` または `UnknownMass` を返します。`massof` メソッドが存在しない場合は、デフォルトで `UnknownMass` になります。
