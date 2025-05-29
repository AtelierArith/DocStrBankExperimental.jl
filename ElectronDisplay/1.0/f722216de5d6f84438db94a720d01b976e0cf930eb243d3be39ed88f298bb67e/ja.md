```
electrondisplay([mime,] x; config...)
```

`x`をElectronウィンドウに表示します。指定された場合はMIME `mime`を使用します。キーワード引数は[`ElectronDisplay.CONFIG`](@ref)を変更せずに上書きするために使用できます。

# 例

```julia
electrondisplay(@doc reduce; single_window=true, focus=false)
```
