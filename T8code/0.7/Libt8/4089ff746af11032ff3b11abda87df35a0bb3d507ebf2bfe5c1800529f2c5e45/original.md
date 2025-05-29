```
t8_cmesh_trees_finish_part(trees, proc)
```

After all classes of trees and ghosts have been set and after the number of tree attributes was set and their total size (per tree) stored temporarily in the att_offset variable we grow the part array by the needed amount of memory and set the offsets appropriately. The workflow should be: call t8*cmesh*trees*start*part, set tree and ghost classes maually via t8*cmesh*trees*add*tree and t8*cmesh*trees*add*ghost, call t8*cmesh*trees*init*attributes, then call this function. Afterwards successively call t8*cmesh*trees*add*attribute for each attribute and also set all face neighbors (TODO: write function).

# Arguments

  * `trees`:[in,out] The trees structure to be updated.
  * `proc`:[in] The number of the part to be finished.

### Prototype

```c
void t8_cmesh_trees_finish_part (t8_cmesh_trees_t trees, int proc);
```
