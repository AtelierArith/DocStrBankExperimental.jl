A transformable block of HTTP headers. Provides a nice API for getting/setting header names and values.

All strings are copied and stored within this datastructure. The index of a given header may change any time headers are modified. When iterating headers, the following ordering rules apply:

  * Headers with the same name will always be in the same order, relative to one another. If "A: one" is added before "A: two", then "A: one" will always precede "A: two".
  * Headers with different names could be in any order, relative to one another. If "A: one" is seen before "B: bee" in one iteration, you might see "B: bee" before "A: one" on the next.
