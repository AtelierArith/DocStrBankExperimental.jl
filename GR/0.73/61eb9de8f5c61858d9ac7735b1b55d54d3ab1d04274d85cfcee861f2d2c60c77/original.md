```
textext(x::Real, y::Real, string)
```

Draw a text at position `x`, `y` using the current text attributes. Strings can be defined to create basic mathematical expressions and Greek letters.

**Parameters:**

`x` :     The X coordinate of starting position of the text string `y` :     The Y coordinate of starting position of the text string `string` :     The text to be drawn

The values for X and Y are in normalized device coordinates. The attributes that control the appearance of text are text font and precision, character expansion factor, character spacing, text color index, character height, character up vector, text path and text alignment.

The character string is interpreted to be a simple mathematical formula. The following notations apply:

Subscripts and superscripts: These are indicated by carets ('^') and underscores ('_'). If the sub/superscript contains more than one character, it must be enclosed in curly braces ('{}').

Fractions are typeset with A '/' B, where A stands for the numerator and B for the denominator.

To include a Greek letter you must specify the corresponding keyword after a backslash ('') character. The text translator produces uppercase or lowercase Greek letters depending on the case of the keyword.

```
+--------+---------+
|Letter  |Keyword  |
+--------+---------+
|Α α     |alpha    |
+--------+---------+
|Β β     |beta     |
+--------+---------+
|Γ γ     |gamma    |
+--------+---------+
|Δ δ     |delta    |
+--------+---------+
|Ε ε     |epsilon  |
+--------+---------+
|Ζ ζ     |zeta     |
+--------+---------+
|Η η     |eta      |
+--------+---------+
|Θ θ     |theta    |
+--------+---------+
|Ι ι     |iota     |
+--------+---------+
|Κ κ     |kappa    |
+--------+---------+
|Λ λ     |lambda   |
+--------+---------+
|Μ μ     |mu       |
+--------+---------+
|Ν ν     |nu       |
+--------+---------+
|Ξ ξ     |xi       |
+--------+---------+
|Ο ο     |omicron  |
+--------+---------+
|Π π     |pi       |
+--------+---------+
|Ρ ρ     |rho      |
+--------+---------+
|Σ σ     |sigma    |
+--------+---------+
|Τ τ     |tau      |
+--------+---------+
|Υ υ     |upsilon  |
+--------+---------+
|Φ φ     |phi      |
+--------+---------+
|Χ χ     |chi      |
+--------+---------+
|Ψ ψ     |psi      |
+--------+---------+
|Ω ω     |omega    |
+--------+---------+
```

For more sophisticated mathematical formulas, you should use the `gr.mathtex` function.
