`classinfo(W)`

returns  information about the  conjugacy classes of  the finite reflection group or Spets `W`. The result is an object with various entries describing properties  of the conjugacy classes of `W`. This object prints at the Repl or in Pluto or Jupyter as a table synthesizing most information.

A  field not in the table  is `.classparams`, containing parameters for the conjugacy  classes. Each parameter is a vector  which has one item for each irreducible   component  of  `W`.  For  what  are  the  parameters  for  an irreducible `W`, see the helpstring of `Chars`.

```julia-repl
julia> classinfo(coxgroup(:A,2))
┌──┬──────────────────────┐
│n0│name length order word│
├──┼──────────────────────┤
│1 │ 111      1     1    .│
│2 │  21      3     2    1│
│3 │   3      2     3   12│
└──┴──────────────────────┘
```

The table contains the columns:

  * `name`, corresponding to the field `.classnames`:  strings describing the conjugacy classes, made out of the information in `:classparams`.
  * `length`, corresponding to the field `.classes`, is the number of elements in the conjugacy class.
  * `order`, corresponding to the field `.orders`, is the order of elements in the conjugacy class.
  * `word`, corresponding to the field `.classtext`, describes a word in the  generators for the  representatives of each  conjugacy class. Each word is a list of integers where the generator `W(i)` is represented by the  integer  `i`.  For  finite  Coxeter  groups,  it  is  the  same as `word.(Ref(W),classreps(W))`,   and  each  such  representative  is  of minimal  length in its conjugacy class and  is a "very good" element in the sense of [GeckMichel1997](biblio.htm#GM97).
