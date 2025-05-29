```
apply(f:: Function, c1:: Curve; axis:: Symbol = :xy, kwargs...)
```

もし ˋaxisˋ が ˋ:xyˋ （デフォルト）であれば：2引数関数 ˋf(x,y)=zˋ をCurveの各エントリに適用します。

もし ˋaxisˋ が ˋ:xˋ または ˋ:yˋ であれば：1引数関数 ˋf(x)=zˋ をCurveの単一の軸に適用します。

出力されるCurveはデフォルト設定を使用して構築され、代替設定は ˋkwargs...ˋ を使用してCurveコンストラクタに渡すことができます。
