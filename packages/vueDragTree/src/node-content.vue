<script>
export default {
  name: 'NodeContent',
  props: {
    node: {
      type: Object,
      required: true
    }
  },
  render(h) {
    const parent = this.$parent
    const tree = parent.tree
    const node = this.node
    const { data, store } = node
    // console.log(tree.$scopedSlots.default({ node, data }))
    return (
      parent.renderContent
        ? parent.renderContent(h, { _self: tree.$vnode.context, node, data, store })
        : tree.$scopedSlots.default
          ? tree.$scopedSlots.default({ node, data })
          : h('span', { class: 'org-tree-node-label-inner' }, [node.label])
    )
  }
}
</script>
