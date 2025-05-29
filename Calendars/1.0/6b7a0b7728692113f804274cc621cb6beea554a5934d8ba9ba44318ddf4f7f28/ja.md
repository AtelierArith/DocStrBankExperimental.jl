```julia
PrintDateLine(date::CDate, io=stdout)
```

与えられた `date` を使って、すべての表現を `io` に出力します。日付の部分は別々に指定することもできます。例えば：

```julia
julia> PrintDateLine(EC, 2022, 2, 2)
```

| CE-2022-02-02 | EC-2022-02-02 | JD-2022-01-20 | AM-5782-12-01 | AH-1443-06-29 | ID-2022-05-03 | EN#0738190 | JN#2459612 |
