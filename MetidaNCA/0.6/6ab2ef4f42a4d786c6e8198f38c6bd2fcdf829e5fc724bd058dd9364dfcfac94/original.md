```
pkplot(subj; ls = false, elim = false, xticksn = :auto, yticksn = :auto, kwargs...)
```

Plot for subject

  * `ls` - concentration in log scale;
  * `elim` - draw elimination curve;
  * `xticksn` - number of ticks on x axis;
  * `yticksn` - number of ticks on y axis;

*Other keywords:*

  * `plotstyle` - predefined plot style from PKPLOTSTYLE;
  * `drawbl` (`false`) - draw baseline, only for PDSubject;
  * `drawth` (`false`) - draw threshold, only for PDSubject;
  * `drawdt` (`false`) - draw drawdose time;
