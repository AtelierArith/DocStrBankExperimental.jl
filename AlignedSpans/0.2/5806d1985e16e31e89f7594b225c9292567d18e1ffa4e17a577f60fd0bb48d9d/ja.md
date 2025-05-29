```
AlignedSpan(sample_rate, span, mode::SpanRoundingMode)
```

`mode.start`に従って左端を丸め、`mode.stop`に従って右端を丸めることによって`AlignedSpan`を作成します。

`mode.start==RoundUp`の場合、結果のスパンの左インデックスは`span`の内部にあることが保証されます。これは、スパンの左端が排他的であるかどうかを確認し、必要に応じて丸めた後にインデックスをインクリメントすることによって実現されます。

同様に、`mode.stop==RoundDown`の場合、結果のスパンの右インデックスは`span`の内部にあることが保証されます。これは、スパンの右端が排他的であるかどうかを確認し、必要に応じて丸めた後にインデックスをデクリメントすることによって実現されます。

注意: `span`は、`AlignedSpans.start_index_from_time`および`AlignedSpans.stop_index_from_time`のメソッドを提供する任意の型である可能性があります。

!!! warning
    入力`span`がサンプルに整列していない場合、つまり入力スパンの`start`と`stop`がサンプルレートの正確な倍数でない場合、結果は最初は直感的でない可能性があります。各基礎サンプルは、ある瞬間に発生するものと見なされ（例えば、`1/sample_rate`の期間にわたってではなく）、丸めはサンプル自体に対して相対的です。

    例えば：

    ```jldoctest
    julia> using TimeSpans, AlignedSpans, Dates

    julia> sample_rate = 1/30
    0.03333333333333333

    julia> input = TimeSpan(0, Second(30) + Nanosecond(1))
    TimeSpan(00:00:00.000000000, 00:00:30.000000001)

    julia> aligned = AlignedSpan(sample_rate, input, RoundInward) # または RoundSpanDown
    AlignedSpan(0.03333333333333333, 1, 2)

    julia> TimeSpan(aligned)
    TimeSpan(00:00:00.000000000, 00:01:00.000000000)

    ```

    `RoundInward`または`RoundSpanDown`のいずれかを指定したにもかかわらず、どちらも右端を下に丸めるため、結果のサンプル整列された`TimeSpan(aligned)`は`TimeSpan(0, Second(60))`です。

    これはどういうことですか？明らかに`Second(60) > Second(30) + Nanosecond(1)`なので、何が起こっているのでしょうか？

    これを理解するためには、1/30Hzではサンプルが00:00、00:30、00:60などで発生することに注意してください。元の入力スパンには*2つ*のサンプル、すなわち00:00のサンプルと00:30のサンプルが含まれています。スパン内で発生するサンプルのみを含めるために内側に丸めることは、両方のサンプルを含めることを意味します（代替動作については[`RoundFullyContainedSampleSpans`](@ref)を参照）。

    TimeSpansに戻すとき、AlignedSpansは`AlignedSpan(1/30, 1, 2)`を`TimeSpan(0, Second(60))`として正規化し、これら2つのサンプルを最初のサンプルから含まれていないサンプル3（`Second(60)`で発生）直前までの時間として表現します。この`TimeSpan`は右端を除外します。

    AlignedSpansは、例えばサンプルを正規化して追加のナノ秒を加えるという異なる選択をすることもできますが、それには独自の問題があります（例えば、`TimeSpan(AlignedSpan(sample_rate, 1, 2))`と`TimeSpan(AlignedSpan(sample_rate, 3, 4))`は連続していないでしょう）。


他にも[`AlignedSpan(sample_rate, span, mode::RoundingModeFullyContainedSampleSpans)`](@ref)を参照してください。 ```
