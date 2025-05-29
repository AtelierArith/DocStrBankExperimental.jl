```
cpuarchitecture()
```

This function tries to infer the CPU microarchitecture with a call to the `cpuid` instruction.  For now, only Intel CPUs are suppored according to the following table.  Others are identified as `:Unknown`.

Table C-1 of Intel's Optimization Reference Manual:

| Family_Model                   | Microarchitecture   |
|:------------------------------ |:------------------- |
| 06*4EH, 06*5EH                 | Skylake             |
| 06*3DH, 06*47H, 06_56H         | Broadwell           |
| 06*3CH, 06*45H, 06*46H, 06*3FH | Haswell             |
| 06*3AH, 06*3EH                 | Ivy Bridge          |
| 06*2AH, 06*2DH                 | Sandy Bridge        |
| 06*25H, 06*2CH, 06_2FH         | Westmere            |
| 06*1AH, 06*1EH, 06*1FH, 06*2EH | Nehalem             |
| 06*17H, 06*1DH                 | Enhanced Intel Core |
| 06_0FH                         | Intel Core          |
