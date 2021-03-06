# [qc.UIImage](CUIImage.md).imageType

## 描述
当前图片的缩放类型，目前包含以下三类的情况。

## 注意
__使用 IMAGE_TYPE_TILED 时，如果平铺的倍数太高，会先进行一级缩放后再进行平铺，我们最多允许横向 32 个平铺，纵向 32 平铺。__  
例如使用一个像素进行平铺成 512 \* 512 的时候，我们实际上为了性能，会先将该像素缩放到 16 \* 16 后再开始平铺（即横纵向的平铺数量为 32）

````
// 普通的缩放，整个图进行直接的拉伸处理
UIImage.IMAGE_TYPE_SIMPLE = 0;

// 使用九宫格进行拉伸，具体的：
//      |         |
//  不变 | 横向拉伸  |  不变
//______|_________|_______
//      |         |
//纵向拉伸| 双向拉伸  | 纵向拉伸
//______|_________|_______
//      |         |
//  不变 | 横向拉伸  |  不变
//      |         |
UIImage.IMAGE_TYPE_SLICED = 1;

// 使用九宫格进行平铺，可参考 SLICED，不同的是
// 处理缩放的时候， SLICED 是拉伸，而 TILED 是平铺
UIImage.IMAGE_TYPE_TILED = 2;
````
