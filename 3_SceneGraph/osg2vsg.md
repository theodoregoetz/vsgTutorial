---
layout: page
title: OpenSceneGraph to VulkanSceneGraph
permalink: /scenegraph/osg2vsg
---

## Smart pointers

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osg::ref_ptr<T>`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/ref_ptr) | [`vsg::ref_ptr<T>`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/ref_ptr.h) |  |
| [`osg::observer_ptr<T>`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/observer_ptr) | [`vsg::observer_ptr<T>`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/observer_ptr.h)  |


## Base classes

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osg::Referenced`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Referenced) | [`vsg::Object`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/Object.h) |  |
| [`osg::Object`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Object) | [`vsg::Object`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/Object.h)  | |
| [`META_Object`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Object), [`META_Node`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Node) | [`vsg::Inherit<T>`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/Inherit.h)  | OSG uses C macros while VSG uses Curiously Recurring Template Pattern |
|  | [`vsg::Allocator`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/Allocator.h)  | Only VSG has memory allocator. |


## Data classes

| OSG | VSG | Notes |
| --- | --- | --- |
| | [`vsg::Data`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/Data.h) | Base class with no OSG equivalent |
| [`osg::Image`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Image) | [`vsg::Value<T>`, `vsg::Array<T>`, `vsg::Array2D<>`, `vsg::Array3D<T>`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/)  |  |
| [`osg::Uniform`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Uniform) | `vsg::Value<T>`, `vsg::Array<T>`, `vsg::Array2D<>`, `vsg::Array3D<T>` |  |
| [`osg::Array<T>`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Array) | [`vsg::Array<T>`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/Array.h) |  |
| [`osg::IndexArray<T>`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Array) | [`vsg::Array<T>`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/core/Array.h) |  |

## Scene graph nodes

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osg::Node`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Node) | [`vsg::Node`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/Node.h)  |  |
| [`osg::Group`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Group) | [`vsg::Group`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/Group.h)  |  |
| [`osg::Switch`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Switch) | [`vsg::Switch`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/Switch.h)  |  |
| [`osg::LOD`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/LOD) | [`vsg::LOD`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/LOD.h)  |  |
| [`osg::PagedLOD`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/PagedLOD) | [`vsg::PagedLOD`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/PagedLOD.h)  |  |
| [`osg::Transform`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Transform) | [`vsg::Transform`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/Transform.h)  | Both base classes for providing model transforms |
| [`osg::MatrixTransform`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/MatrixTransform) | [`vsg::MatrixTransform`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/MatrixTransform.h)  |  |
| [`osg::MatrixTransform`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/MatrixTransform) | [`vsg::AbsoluteTransform`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/AbsoluteTransform.h)  |  osg::MatrixTransform::[setReferenceFrame(ABSOLUTE_RF)](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Transform#97) equivalent to vsg::AbsoluteTransform |
| [`osg::PositionAttitudeTransform`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/PositionAttitudeTransform) |  | No VSG equivalent |
| [`osg::AutoTransform`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/AutoTransform) |  | No VSG equivalent |
| [`osg::Billboard`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Billboard) |  | No VSG equivalent - use instanced geometry and vertex shader. |

## Geometry

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osg::Drawable`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Drawable) | [`vsg::Command`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/commands/Command.h)  |  |
| [`osg::Geometry`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Geometry) | [`vsg::Geometry`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/Geometry.h)  |  |
| [`osg::DrawArrays`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/PrimitiveSet#L221) | [`vsg::Draw`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/commands/Draw.h) |  |
| [`osg::DrawElements`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/PrimitiveSet#L336) | [`vsg::DrawIndexed`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/commands/DrawIndexed.h) |  |
| | [`vsg::Commands`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/commands/Commands.h) | No OSG equivalent. |
| | [`vsg::VertexDraw`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/VertexDraw)  |  No direct OSG equivalent, closest is osg::Geometry |
| | [`vsg::VertexIndexDraw`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/VertexIndexDraw.h)  |  No OSG equivalent, closest is osg::Geometry. |
| | [`vsg::BindVertexBuffers`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/commands/BindVerteBuffers.h) | No OSG equivalent. |
| | [`vsg::BindIndexBuffers`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/commands/BindIndexBuffers.h) | No OSG equivalent. |

## State

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osg::StateSet`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/StateSet) | [`vsg::StateGroup`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/nodes/StateGroup.h)  |  osg::Group with an osg::StateSet is broadly similar to vsg::StateGroup |
| [`osg::StateAttribute`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/StateAttribute) | [`vsg::StateCommand`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/state/)  |  Both are state base classes, but only vaguely similar |
| [`osg::Texture`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Texture), osg::Texture1D, osg::Texture2D, osg::Texture3D, osg::TextureCubeMap, Texture2DArray | [`vsg::DescriptorImage`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/state/DescriptorImage.h), vsg::ImageView, vsg::Image  | No direct mapping but together fulfill the same role. |
| [`osg::Uniform`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Uniform) | [`vsg::DescriptorBuffer`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/state/DescriptorBuffer.h)  |  |
| [`osg::Light`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Light.h), osg::LightSource | [`vsg::Light`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/state/DescriptorBuffer.h), vsg::AmbientLight, vsg::DirectionalLight, vsg;:PointLight, vsg::SpotLight  |  |

## Text

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osgText::Font`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgText/Font) | [`vsg::Font`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/text/Font.h)  |  |
| [`osgText::Text`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgText/Text) | [`vsg::Text`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/text/Text.h)  |  |
| [`osgText::Text3D`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgText/Text3D) |  | No VSG equivalent |
| | [`vsg::TextGroup`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/text/TextGroup.h)  | No OSG equivalent for efficient rendering of large number of labels |

## IO

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osgDB::readObjectFile(..)`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/ReadFile#L232) | [`vsg::read(..)`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/read.h)  |  |
| [`osgDB::readNodeFile(..)`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/ReadFile#L308) | [`vsg::read_cast<vsg::Node>(..)`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/read.h)  |  |
| [`osgDB::readImageFile(..)`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/ReadFile#L268) | [`vsg::read_cast<vsg::Data>(..)`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/read.h)  |  |
| [`osgDB::writeObjectFile(..)`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/WriteFile) | [`vsg::write(..)`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/write.h)  |  |
| [`osgDB::writeNodeFile(..)`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/WriteFile) | [`vsg::write(..)`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/write.h)  |  |
| [`osgDB::writeImageFile(..)`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/WriteFile) | [`vsg::write(..)`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/write.h)  |  |
| [`osgDB::Options`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/Options) | [`vsg::Options`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/Options.h)  |  |
| [`osgDB::FileCache`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/FileCache) | [`vsg::Options::fileCache`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/Options.h#L75)  |  |
| [`osgDB::ObjectCache`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/ObjectCache) | [`vsg::SharedObjects`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/utils/SharedObjects.h)  |  |
| [`osgDB::ReaderWriter`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/ReaderWriter) | [`vsg::ReaderWriter`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/ReaderWriter.h)  |  |
| [`osgDB::Registry`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/Registry) | [`vsg::ObjectFactory`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/ObjectFactory.h)  |  |
| [`std::string & UTF8`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/ConvertUTF8) | [`vsg::Path`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/Path.h)  |  OSG must be compiled with OSG_USE_UTF8_FILENAME, vsg::Path works like std::filesystem::path |
| [`osgDB::DatabasePager`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgDB/DatabasePager) | [`vsg::DatabasePager`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/io/DatabasePager.h)  |  |

## Application

| OSG | VSG | Notes |
| --- | --- | --- |
| [`osg::Camera`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osg/Camera.h) | [`vsg::Camera`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/Camear.h)  |  |
| [`osgViewer::View`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgViewer/View.h) | [`vsg::View`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/View.h)  |  |
| [`osgViewer::Viewer`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgViewer/Viewer.h) | [`vsg::Viewer`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/Viewer.h)  |  |
| [`osgViewer::CompositeViewer`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgViewer/CompositeViewer.h) | [`vsg::Viewer`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/Viewer.h)  |  |
| [`osgGA::TrackballManipulator`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/osgGA/TrackballManipulator) | [`vsg::Trackball`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/Trackball.h)  |  |
| | [`vsg::CommandGraph`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/CommandGraph.h)  | No OSG equivalent |
| | [`vsg::RenderGraph`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/RenderGraph.h)  | No OSG equivalent |
| | [`vsg::RecordAndSubmitTask`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/RecordAndSubmitTask.h)  | No OSG equivalent |
| | [`vsg::ExecuteCommands`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/app/ExecuteCommands.h)  | No OSG equivalent |

## Threading

| OSG | VSG | Notes |
| --- | --- | --- |
| [`OpenThreads::Thread`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Thread) | std::thread | |
| [`OpenThreads::Mutex`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Mutex) | std::mutex| |
| [`OpenThreads::ScopedLock`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Block.h) | std::lock_guard | |
| [`OpenThreads::Atomic`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Atomic) | std::atomic | |
| [`OpenThreads::Condition`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Condition) | std::condition_variable | |
| [`OpenThreads::Barrier`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Barrier) | [`vsg::Barrier`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/Barrier.h) | |
| [`OpenThreads::Block`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Block) | [`vsg::Latch`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/Latch.h) | |
| [`OpenThreads::Affinity`](https://github.com/openscenegraph/OpenSceneGraph/blob/master/include/OpenThreads/Affinity) | [`vsg::Affinity`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/Affinity.h) | |
|  [`osg::OperationThread`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/osg/OperationThread) | [`vsg::OperationThread`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/OperationThread.h) |  |
|  [`osg::OperationThread`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/osg/OperationThread) | [`vsg::OperationQueue`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/OperationQueue.h) |  |
|  [`osg::Operation`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/osg/OperationThread) | [`vsg::Operation`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/OperationQueue.h) |  |
|  | [`vsg::ActivityStatus`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/ActivityStatus.h) | No OSG equivalent, used to cooperatively release barriers & blocks. |
| | [`vsg::FrameBlock`](https://github.com/vsg-dev/VulkanSceneGraph/blob/master/include/vsg/threading/FrameBlock.h) | No direct OSG equivalent, loosely OpenThreads::Block. |

Prev : [Ray Tracing](RayTracing.md) | Next : [Next Chapter : Application](../4_Application/index.md)

