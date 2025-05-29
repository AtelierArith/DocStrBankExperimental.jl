```
latexIsotopeTable(Z1::Int, Z2::Int; continuation=false)
latexIsotopeTable(itrZ::UnitRange; continuation=false)
```

Isotope table for all isotopes with atomic number from `Z1` to `Z2`.

#### Example:

```
o = latexIsotopeTable(1:3);
println(o)
  \setlength{\tabcolsep}{3pt}
  \renewcommand{\arraystretch}{1.2}
  \begin{table}[H]
    \centering
    \caption{\label{table:Isotopes-a-1}Properties of selected atomic isotopes. The Table is based on three databases: (a) AME2020 (atomic mass evaluation); (b) IAEA-INDC(NDS)-794 (magnetic dipole moments); (c) IAEA-INDC(NDS)-833 (electric quadrupole moments).}
    \begin{tabular}{r|lr|rrrr|r|r|r|r}
      \multicolumn{12}{r}\vspace{-18pt}\\
      \hline
      \hline
      $Z$ & element & symbol & $A$ & $N$ & radius & atomic mass & $I\,^\pi$ & $\mu_I $ & $Q$ & $RA$\\&  &  &  &  & (fm) & $(m_u)$ & $(\hbar)\ \ $ & $(\mu_N)$ & (barn) & (\%)\\\hline
      1 & hydrogen & $^{1}$H & 1\, & 0 & 0.8783 & 1.007825032 & 1/2$^+$ & 2.792847351 & 0.0 & 99.9855 \\
        &  & $^{2}$H & 2\, & 1 & 2.1421 & 2.014101778 & 1//1$^+$ & 0.857438231 & 0.0028578 & 0.0145 \\
        &  & $^{3}$H & 3$*\!\!$ & 2 & 1.7591 & 3.016049281 & 1/2$^+$ & 2.97896246 & 0.0 & trace \\
      \hline
      2 & helium & $^{3}$He & 3\, & 1 & 1.9661 & 3.016029322 & 1/2$^+$ & -2.12762531 & 0.0 & 0.0002 \\
        &  & $^{4}$He & 4\, & 2 & 1.6755 & 4.002603254 & 0//1$^+$ & 0.0 & 0.0 & 99.9998\% \\
      \hline
      3 & lithium & $^{6}$Li & 6\, & 3 & 2.589 & 6.015122887 & 1//1$^+$ & 0.822043 & -0.000806 & 4.85 \\
        &  & $^{7}$Li & 7\, & 4 & 2.444 & 7.016003434 & 3/2$^-$ & 3.256407 & -0.04 & 95.15 \\
      \hline
      \multicolumn{12}{l}{*radioactive }\\
    \end{tabular}
  \end{table}
```

The typeset result is shown in the figure below.

![Image](../../assets/latexIsotopeTable.png)
