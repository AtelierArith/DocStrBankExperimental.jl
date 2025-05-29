```
show_psi(N::Integer, B::Int)
show_psi(N::ZZRingElem, B::Int)
```

\code{psi*lower} と \code{psi*upper} を使用して、$0\le i\le \log_2(N)$ の範囲で $\psi(2^i, B)$ が存在する区間を見つけます。ここで、$\psi(N, B) = \#\{1\le i\le N | \text{$i$ は $B$-smooth}}$ です。
