# anonymous-13-10-2022forWWW2023
Note that you need to unzip data.7zip to get the datasets.
# Requirements
cuda11.3


dgl-cu113


pytorch>=1.10.0



# Graph Classification

Default dataset is PROTEINS. You need to change the corresponding parameters in *pre_train.py* and *prompt_fewshot.py* to train and evaluate on other datasets.
## Pre-Train
python pre_train.py 

## Prompting
python prompt_fewshot.py

# Node Classification
Default dataset is ENZYMES. You need to change the corresponding parameters in *pre_train.py* and *prompt_fewshot.py* to train and evaluate on PROTEINS.
Note that node level doesn't need pre-train again. We use the graph level pre-train model.

## Prompting
python run.py --pretrain_model GIN --gpu_id 1 --reg_loss NLL --bp_loss NLL --prompt FEATURE-WEIGHTED-SUM --epochs 100 --lr 0.1 --update_pretrain False --seed 0 --dropout 0 --dataset_seed 0 --train_shotnum 1 --val_shotnum 1 few_shot_tasknum 10 --nhop_neighbour 1 --gcn_graph_num_layers 3 --gcn_hidden_dim 32 --prompt_output_dim 2 --batch_size 1024 --max_ngv 126 --max_nge 282 --max_ngvl 3 --max_ngel 2 --node_feature_dim 18 --graph_label_num 6 --graph_num 53 --graph_dir ../data/ENZYMES/allraw --save_data_dir ../data/ENZYMES/all --save_pretrain_model_dir ../dumps/ENZYMESPreTrain/GIN --downstream_save_model_dir ../dumps/ENZYMESNodeClassification/Prompt/GIN-FEATURE-WEIGHTED-SUM/all/10train10val10task --save_fewshot_dir ../data/ENZYMES/nodefewshot --process_raw False --split False

