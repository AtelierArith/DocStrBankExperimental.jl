```
init()
```

Initialize the tracing library.

This routine is called automatically in different circumstances, which include:

  * Call to MPI_Init when the appropriate instrumentation library is linked or preload with the application.
  * Usage of the DynInst launcher.
  * If either the `libseqtrace.so`, `libomptrace.so` or `libpttrace.so` are linked dynamically or preloaded with the application.

No major problems should occur if the library is initialized twice, only a warning appears in the terminal output noticing the intent of double initialization.
