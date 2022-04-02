## Running results

Google Spreadsheet: https://docs.google.com/spreadsheets/d/1Mu8cAAiqexs-nCn2iukEE0VU1wDp9n_znJmyEfYXFP4/edit?usp=sharing

This spreadsheet includes the running results for 8 apks, each including 5 runs with the same monkey seed. For each run, the targeted apk ran monkey for one hour, and the results are the bug reproduction time in each run. 

For example, `['1', '21']` means in `Run1` of `sunflower#239.apk`, `bug #239` was triggered 2 times, happening at the 1st and 21st minutes of this run. 

__Please investigate the columns highlighted in yellow.__

## Results for Monkey

Each folder in this repo includes the results for 5 runs. For each run, it will has 4 output files, only 2 files that need our attention:

* __monkey.log__: it contains the running process of each monkey action.
* __logcat.log__: it logs the crash information during the running process.

For the convenience, the reference _crash_stack.log_ of each bug is also included in each folder.

## Check crashes of each run

Run the check_crash.py to check the crash time in each run (modified a little bit based on the original themis version):

`python3 check_crash.py --monkey -o <folder_name> --app <app_name> --id \#<bug_id> --simple`

For example:

`python3 check_crash.py --monkey -o sunflower --app sunflower --id \#239 --simple`

It will parse the `logcat.log` for each run and find the crash time. According to the crash time, you can investigate the actions in `monkey.log` to find the potential reason for each reproduction: __Under the same monkey seed and trajectories, why some runs can reproduce the bug and others cannot?__

## Themis Benchmark
For further detailed information about each bug, please check the original themis benchmark: 

https://github.com/the-themis-benchmarks/home
