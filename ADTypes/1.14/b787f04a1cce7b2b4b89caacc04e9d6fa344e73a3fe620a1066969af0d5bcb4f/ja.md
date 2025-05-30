```
AutoReverseDiff{compile}
```

自動微分のために[ReverseDiff.jl](https://github.com/JuliaDiff/ReverseDiff.jl)バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoReverseDiff(; compile::Union{Val, Bool} = Val(false))
```

# フィールド

  * `compile::Union{Val, Bool}`: テープの事前記録と再利用を許可するかどうか（これにより微分プロセスが高速化されます）。

      * `compile=false`または`compile=Val(false)`の場合、微分演算子への各呼び出しで新しいテープを記録する必要があります。
      * `compile=true`または`compile=Val(true)`の場合、例の入力でテープを事前に記録し、その後のすべての微分呼び出しで再利用できます。

    このキーワード引数のブールバージョンは型パラメータとして扱われます。

!!! warning
    テープの事前記録は、*例の入力で実行されたときの微分された関数が取った経路*のみをキャプチャします。該当する関数に値依存の分岐動作がある場合、事前に記録されたテープを再利用すると不正確な結果をもたらす可能性があります。そのような状況では、デフォルト設定`compile=Val(false)`を維持するべきです。詳細については、ReverseDiffの[`AbstractTape` APIドキュメント](https://juliadiff.org/ReverseDiff.jl/dev/api/#The-AbstractTape-API)を参照してください。


!!! info
    名前が示唆するように、`compile`設定は、テープが記録された後に[`ReverseDiff.compile`](https://juliadiff.org/ReverseDiff.jl/dev/api/#ReverseDiff.compile)でコンパイルされるかどうかを規定するものではありません。これはプライベートな実装の詳細として残されています。

