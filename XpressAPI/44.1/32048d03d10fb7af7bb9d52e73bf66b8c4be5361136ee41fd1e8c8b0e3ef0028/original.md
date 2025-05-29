```
XPRS_CUTSELECT
```

A bit vector providing detailed control of the cuts created for the root node of a MIP solve. (integer)

Use TREECUTSELECT to control cuts during the tree search.

Default value: `-1`

Values are a bitset: bit 5 : Clique cuts. bit 6 : Mixed Integer Rounding (MIR) cuts. bit 7 : Lifted cover cuts. bit 8 : Turn on row aggregation for MIR cuts. bit 11 : Flow path cuts. bit 12 : Implication cuts. bit 13 : Turn on automatic Lift-and-Project cutting strategy. bit 14 : Disable cutting from cut rows. bit 15 : Lifted GUB cover cuts. bit 16 : Zero-half cuts. bit 17 : Indicator constraint cuts. bit 18 : Strong Chvatal-Gomory cuts. bit 20 : Farkas cuts.
