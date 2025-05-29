```
avgseq, results = dba(sequences, dist::DTWDistance; kwargs...)
```

与えられた `sequences` のコレクションと現在の平均シーケンスの推定値に基づいて、DTWバリセント平均化（DBA）を実行します。

使用例:

```
x = [1., 2., 2., 3., 3., 4.]
y = [1., 3., 4.]
z = [1., 2., 2., 4.]
avg,result = dba([x,y,z], DTW(3))
```
