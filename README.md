class AbstractSignal:
    """
    Class that provides functionality for accessing its inner data.

    Setting `_data` must be provided by child classes.
    """

    _data: pd.Series

    def __getitem__(self, item):
        return self.values.__getitem__(item)

    # usually, the data of a signal should not be modified. But currently, it is
    # necessary when dxv would be larger than dx_max in a resimulation.
    def __setitem__(self, key, value):
        return self.values.__setitem__(key, value)

    def __len__(self):
        return self.values.__len__()

    def __iter__(self):
        return self.values.__iter__()

    @property
    def values(self):
        return self._data.values

    @property
    def index(self):
        return self._data.index

    def __add__(self, other):
        return self._data.__add__(other)

    def __sub__(self, other):
        return self._data.__sub__(other)

    def __mul__(self, other):
        return self._data.__mul__(other)

    def __truediv__(self, other):
        return self._data.__truediv__(other)

    def __radd__(self, other):
        return self._data.__radd__(other)

    def __rsub__(self, other):
        return self._data.__rsub__(other)

    def __rmul__(self, other):
        return self._data.__rmul__(other)

    def __rtruediv__(self, other):
        return self._data.__rtruediv__(other)

    def __neg__(self):
        return self._data.__neg__()

    def sin(self):
        return np.sin(self._data)

    def cos(self):
        return np.cos(self._data)

    def tan(self):
        return np.tan(self._data)

    def apply(self, *args):
        return self._data.apply(*args)
