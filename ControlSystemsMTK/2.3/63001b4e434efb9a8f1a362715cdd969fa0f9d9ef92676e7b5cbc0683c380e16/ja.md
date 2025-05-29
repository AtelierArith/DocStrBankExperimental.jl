```
sconnect(sys1::T, sys2::T; name)
```

システムを直列に接続します。これは、ControlSystems.jlの用語で`sys2*sys1`または`series(sys1, sys2)`に相当します。
