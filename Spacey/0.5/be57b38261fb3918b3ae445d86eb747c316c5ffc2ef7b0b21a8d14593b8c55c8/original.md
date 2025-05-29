Adjust input vectors and atomic basis to be an exact match to symmetry found. Adjust symmetries to be exact orthonormal transforms (to machine precision)

In most applications, where robustness/accuracy is the most important consideration (rather than speed), one should probably always call the "robust" pointGroup finder and then follow up with a call to this routine. If the input is trustworthy (highly accurate), then calling this routine would be unnecessary.
