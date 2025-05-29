```
AbsIntStackUnwind(sv::AbsIntState)
```

与えられた `AbsIntState` の抽象解釈スタック内のすべての呼び出し元を反復処理し、子を親の前に訪問します（すなわち、与えられた `AbsIntState` から木を上昇します）。サイクルは任意の順序で訪問される可能性があることに注意してください。
