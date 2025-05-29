```
GCPair(smarts,name;group_order = 1)
```

Struct used to hold a description of a group. Contains the SMARTS string necessary to match the group within a SMILES query, and the assigned name. the `group_order` parameter is used for groups that follow a Constantinou-Gani approach: the list of `GCPair` with `group_order = 1` will be matched with strict coverage (failing if there is missing atoms to cover) while second order groups and above will not be stringly checked for total coverage. Each order group will be matched independendly.
