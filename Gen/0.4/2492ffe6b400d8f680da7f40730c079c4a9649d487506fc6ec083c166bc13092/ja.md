```
@kern function k(trace, args...)
    ...
end
```

複合MCMCカーネルを構築します。

結果として得られるオブジェクトは、複合MCMCカーネルとして注釈されたJulia関数であり、Julia関数として呼び出すことも、他の複合カーネル内で適用することもできます。
