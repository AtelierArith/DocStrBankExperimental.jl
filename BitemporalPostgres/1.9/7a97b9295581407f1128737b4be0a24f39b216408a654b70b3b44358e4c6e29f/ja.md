commit*workflow!(w::Workflow)   commits the bitemporal transaction identified by ref*version   begun with the creation of w

  * sets w's version's validityInterval to is_committed
  * ends all overlapping intervals to tsdb*invalidfrom w.tsdb*validfrom
  * creates a new interval for the non_overlapping part of a partially interval if any
