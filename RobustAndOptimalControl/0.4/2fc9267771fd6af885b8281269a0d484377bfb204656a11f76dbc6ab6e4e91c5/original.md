```
P = hinfpartition(G, WS, WU, WT)
```

Transform a SISO or MIMO system $G$, with weighting functions $W_S, W_U, W_T$ into an LFT with an isolated controller, and write the resulting system, $P(s)$, on a state-space form. Valid inputs for $G$ are transfer functions (with dynamics, can be both MIMO and SISO, both in tf and ss forms). Valid inputs for the weighting functions are empty arrays, numbers (static gains), and `LTISystem`s.

Note, `system_mapping(P)` is equal to `-G`.

# Extended help

For ill-conditioned MIMO plants, the $S, CS, T$ weighting may result in controllers that "invert" the plant, which may result in poor robustness. For such systems, penalizing $GS$ and $T$ may be more appropriate. Ref: "Inverting and noninverting H∞ controllers", Urs Christen, Hans Geering
