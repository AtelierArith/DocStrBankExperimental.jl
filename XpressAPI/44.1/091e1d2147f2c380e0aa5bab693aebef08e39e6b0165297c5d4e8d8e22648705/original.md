```
XPRS_PRESOLVEOPS
```

This bit vector control specifies the operations which are performed during the presolve. (integer)

Default value: `511` (bits `0` `8` incl. are set)

Values are a bitset: bit 0 : Singleton column removal. bit 1 : Singleton row removal. bit 2 : Forcing row removal. bit 3 : Dual reductions. bit 4 : Redundant row removal. bit 5 : Duplicate column removal. bit 6 : Duplicate row removal. bit 7 : Strong dual reductions. bit 8 : Variable eliminations. bit 9 : No IP reductions. bit 10 : No domain changes for MIP entities (e.g., semi-continuous detection or shifting integers). bit 11 : No advanced IP reductions. bit 12 : No eliminations on integers. bit 13 : No reductions based on solution enumeration. bit 14 : Linearly dependant row removal. bit 15 : No integer variable and SOS detection. bit 16 : No implied bounds. bit 17 : No clique presolve. bit 18 : No mod2 presolve.
