# meta-dnn
Yocto layer that includes Vitis AI DNN into the Linux image. This document assums Petalinux 2020.2 and Vitis AI 1.3.1.

# Building the Petalinux project

This document assumes that the hardware design has been done and that the BSP and the XSA files are available to start the software setup with Petalinux. If this is not the case, then checkout [Vitis AI DPU-TRD](https://github.com/Xilinx/Vitis-AI/tree/1.3.1/dsa/DPU-TRD/prj/Vivado) webpage for Vivado design. A BSP file is provided in this [script](https://github.com/Xilinx/Vitis-AI/blob/1.3.1/dsa/DPU-TRD/prj/Vivado/dpu_petalinux_bsp/download_bsp.sh). Make sure that the BSP and XSA files were generated with Vivado 2020.2.

```bash
$ source /storage/Xilinx/PetaLinux/2020.2/tool/settings.sh
$ petalinux-create -t project -s /storage/Xilinx/PetaLinux/2020.2/xilinx-zcu102-trd.bsp -n dpu-trd
$ export TRD_HOME=/storage/repos/xilinx/Vitis-AI-1.3.1/Vitis-AI/dsa/DPU-TRD
$ petalinux-config --get-hw-description=$TRD_HOME/prj/Vivado/prj  --silentconfig
$ petalinux-build
$ petalinux-package --boot --fsbl zynqmp_fsbl.elf --u-boot u-boot.elf --pmufw pmufw.elf --fpga system.bit
```

## Links

- https://github.com/UviDTE-FPSoC/Zynq7000-dnn-inference/wiki/petalinux-project-configuration-to-run-deep-neural-networks
- https://github.com/UviDTE-FPSoC/Zynq7000-dnn-inference/wiki/Petalinux-project-configuration-to-run-Deep-Neural-Networks
- https://github.com/Xilinx/Vitis-AI/tree/1.3.1/dsa/DPU-TRD/prj/Vivado
- https://github.com/Xilinx/Vitis-AI/tree/1.3.1/dsa/DPU-TRD/prj/Vitis
- https://github.com/gewuek/vitis_ai_custom_platform_flow/blob/master/README.md
- https://github.com/Xilinx/Vitis-Tutorials/tree/2020.2/Vitis_Platform_Creation/Introduction/02-Edge-AI-ZCU104
- https://github.com/SV-1509/Object-Detection-on-FPGA/blob/main/README.md
- https://github.com/luunguyen97/DPU-TRD-ZCU104/blob/master/prj/Vivado/scripts/dpux1_zcu104.tcl
- https://github.com/wutianze/dnndk-pynqz2/blob/master/build-pynqz2-system.md
- https://github.com/amamory-ampere/Zynq-7000-DPU-TRD
- https://github.com/DuyTrandeLion/PYNQ-Z1

## Authors

 - Alexandre Amory (Frebruary 2022), [Real-Time Systems Laboratory (ReTiS Lab)](https://retis.santannapisa.it/), [Scuola Superiore Sant'Anna (SSSA)](https://www.santannapisa.it/), Pisa, Italy.

## Funding
 
This software package has been developed in the context of the [AMPERE project](https://ampere-euproject.eu/). This project has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 871669.
