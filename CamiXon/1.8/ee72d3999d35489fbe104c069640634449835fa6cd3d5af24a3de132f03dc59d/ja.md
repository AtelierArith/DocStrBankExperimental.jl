```
latexIsotopeTable(Z1::Int, Z2::Int; continuation=false)
latexIsotopeTable(itrZ::UnitRange; continuation=false)
```

`Z1`から`Z2`までの原子番号を持つ全ての同位体の表。

#### 例:

```
o = latexIsotopeTable(1:3);
println(o)
  \setlength{\tabcolsep}{3pt}
  \renewcommand{\arraystretch}{1.2}
  \begin{table}[H]
    \centering
    \caption{\label{table:Isotopes-a-1}選択された原子同位体の特性。表は3つのデータベースに基づいています: (a) AME2020 (原子質量評価); (b) IAEA-INDC(NDS)-794 (磁気双極子モーメント); (c) IAEA-INDC(NDS)-833 (電気四重極モーメント)。}
    \begin{tabular}{r|lr|rrrr|r|r|r|r}
      \multicolumn{12}{r}\vspace{-18pt}\\
      \hline
      \hline
      $Z$ & element & symbol & $A$ & $N$ & radius & atomic mass & $I\,^\pi$ & $\mu_I $ & $Q$ & $RA$\\&  &  &  &  & (fm) & $(m_u)$ & $(\hbar)\ \ $ & $(\mu_N)$ & (barn) & (\%)\\\hline
      1 & 水素 & $^{1}$H & 1\, & 0 & 0.8783 & 1.007825032 & 1/2$^+$ & 2.792847351 & 0.0 & 99.9855 \\
        &  & $^{2}$H & 2\, & 1 & 2.1421 & 2.014101778 & 1//1$^+$ & 0.857438231 & 0.0028578 & 0.0145 \\
        &  & $^{3}$H & 3$*\!\!$ & 2 & 1.7591 & 3.016049281 & 1/2$^+$ & 2.97896246 & 0.0 & trace \\
      \hline
      2 & ヘリウム & $^{3}$He & 3\, & 1 & 1.9661 & 3.016029322 & 1/2$^+$ & -2.12762531 & 0.0 & 0.0002 \\
        &  & $^{4}$He & 4\, & 2 & 1.6755 & 4.002603254 & 0//1$^+$ & 0.0 & 0.0 & 99.9998\% \\
      \hline
      3 & リチウム & $^{6}$Li & 6\, & 3 & 2.589 & 6.015122887 & 1//1$^+$ & 0.822043 & -0.000806 & 4.85 \\
        &  & $^{7}$Li & 7\, & 4 & 2.444 & 7.016003434 & 3/2$^-$ & 3.256407 & -0.04 & 95.15 \\
      \hline
      \multicolumn{12}{l}{*放射性 }\\
    \end{tabular}
  \end{table}
```

組版結果は以下の図に示されています。

![Image](../../assets/latexIsotopeTable.png)
