```
@pt(expr...)
```

Pretty print tables in `expr` to `stdout` using the global configurations selected with the macro `@ptconf`.

Multiple tables can be printed by passing multiple expressions like:

```
@pt table1 table2 table3
```

The user can select the table header by passing the expression:

```
:header = [<Vector with the header>]
```

Notice that the header is valid only for the next printed table. Hence:

```
@pt :header = header1 table1 :header = header2 table2 table3
```

will print `table1` using `header1`, `table2` using `header2`, and `table3` using the default header.

!!! info
    When more than one table is passed to this macro, then multiple calls to `pretty_table` will occur. Hence, the cropping algorithm will behave exactly the same as printing the tables separately.


# Examples

```julia
julia> @ptconf tf = tf_simple

julia> @pt :header = ["Time","Velocity"] [1:1:10 ones(10)] :header = ["Time","Position"] [1:1:10 1:1:10]
======= ===========
  Time   Velocity
======= ===========
   1.0        1.0
   2.0        1.0
   3.0        1.0
   4.0        1.0
   5.0        1.0
   6.0        1.0
   7.0        1.0
   8.0        1.0
   9.0        1.0
  10.0        1.0
======= ===========
======= ===========
  Time   Position
======= ===========
     1          1
     2          2
     3          3
     4          4
     5          5
     6          6
     7          7
     8          8
     9          9
    10         10
======= ===========

julia> @pt ones(3,3) + I + [1 2 3; 4 5 6; 7 8 9]
========= ======== =========
  Col. 1   Col. 2   Col. 3
========= ======== =========
     3.0      3.0      4.0
     5.0      7.0      7.0
     8.0      9.0     11.0
========= ======== =========
```
