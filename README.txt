--------Setting up the environment and downloading general dependencies.

Step 1: Check the TEE status across VMS using below command.
        dmesg | grep TDX
        dmesg | grep SEV

Step 2: In case TEE is not in active state, make changes in the grub files.
        nano /etc/default/grub.d/50-cloudimg-settings.cfg

   ---- ADD following lines to the grub file:
        GRUB_CMDLINE_LINUX_DEFAULT="modprobe.blacklist=btrfs mem_encrypt=on kvm_amd.sev=1"
   -----Update grub file
        sudo update-grub
   -----Take a reboot of the system
        sudo reboot
   -----Check TEE Status using Step 1

Step 3: Creating a virtual environment for python files to execute.
        sudo apt-get update
        sudo apt-get install -y python3-pip
        python3 -m venv venv
        source venv/bin/activate

Step 4: Installing Python Dependencies
        pip install matplotlib, re, seaborn, numpy

Step 5: Repeating steps across all the VMs.

------- Once all the VMs are set up, you can use the included folders and files within them to run the provided benchmarks on each VM. The README file in each benchmarking folder explains the entire benchmarking process.
        
  



       