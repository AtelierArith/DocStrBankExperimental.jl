This method takes an `.xyz` file (with cartesian coordinates of atoms in a molecule) and returns a `Molecule`. The `.xyz` file should be formatted as follows

```julia
2 

H      -1.788131055      0.000000000     -4.028513155
H      -1.331928651      0.434077746     -3.639854078
```

In the first line, the file should contain the numer of atoms that are in the molecule. In the second line, there is a comment, which can be the *name of the compound*,  *molecular formula*, etc. To further information about `.xyz` files, [*click here*](https://www.reviversoft.com/file-extensions/xyz). For example, if we take the  example file `h2.xyz`, it is possible to give it as an input by calling `molecule` method.

```julia
molecule("h2.xyz")
```

The example above works if the file is in the current directory that you are working on. In other case, you can just give the path to the file of interest.

```julia
molecule(PATH)
```
