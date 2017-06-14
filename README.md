# pyqsub
Python functions for working with qsub. Originally designed for use with the SGE compute cluster at NYUMC.

The primary goal of this module is to facilitate data analysis pipeline development by making it easier to submit cluster jobs and monitor their completion status, from within Python. 

# Installation

Simply clone this repo

```bash
git clone --recursive https://github.com/stevekm/pyqsub.git
```

And place both `pyqsub.py` and `sh.py` adjacent to your Python script, after which you can `import pyqsub` and use its functions. 

# Usage
You can demo the module by running it directly as a script:

```bash
$ ./pyqsub.py
Command is:

qsub -j y -N python -o :${PWD}/ -e :${PWD}/ <<E0F

    set -x
    cat /etc/hosts
    sleep 300

E0F

Job ID: 1508702
Job Name: python
waiting for job to start
....
job 1508702 has started


...
...


waiting for all jobs ['1508703', '1508704', '1508705', '1508706', '1508707'] to start...
....all jobs have started; elapsed time: 0:00:12.971239
waiting for all jobs ['1508703', '1508704', '1508705', '1508706', '1508707'] to finish...
..........all jobs have finished; elapsed time: 0:00:31.984778

```

The module can be integrated into larger Python scripts. See [this example](https://github.com/stevekm/reportIT/blob/62556ae555b7c9df4fd6623a43fd0fe6d5baa922/code/run_samplesheet.py#L125) for ideas on how to implement this.

# Software
Tested under Python 2.6, 2.7, and 3.4.3, with the `sh.py` module as a dependency. 
