A QN object stores a collection of up to four named values such as ("Sz",1) or ("N",0). These values can include a third integer "m" which makes them obey addition modulo m, for example ("P",1,2) for a value obeying addition mod 2. (The default is regular integer addition).

Adding or subtracting pairs of QN objects performs addition and subtraction element-wise on each of the named values. If a name is missing from the collection, its value is treated as zero.
