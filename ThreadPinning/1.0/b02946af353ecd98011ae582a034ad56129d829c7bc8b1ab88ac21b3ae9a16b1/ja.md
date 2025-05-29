```
pinthreads_likwidpin(str::AbstractString; onebased = false)
```

与えられた `likwid-pin` 互換の文字列に基づいて、Julia スレッドを CPU スレッドに固定します。詳細については、[LIKWID ドキュメント](https://github.com/RRZE-HPC/likwid/wiki/Likwid-Pin)を参照してください。

キーワード引数 `onebased` が `true` に設定されている場合、論理インデックスおよびドメインインデックスはゼロではなく1から始まります（likwid-pin のデフォルト）。ただし、"物理" CPU ID は常にゼロから始まる明示的なピンニングモードには影響しないことに注意してください。

**例**

  * `pinthreads_likwidpin("S0:0-3")`
  * `pinthreads_likwidpin("M1:0,2,4")`
  * `pinthreads_likwidpin("S:scatter")`
  * `pinthreads_likwidpin("E:N:4:1:2")`
